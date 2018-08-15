# Nitrous
Shell script to install a [Nitrous Masternode](https://) on a Linux server running Ubuntu 16.04. Use it on your own risk.
The script will install version 3.0.0.0
***

## Installation
```
wget -N https://raw.githubusercontent.com/zoldur/Nitrous/master/nitrous_install.sh
bash nitrous_install.sh
```
***

## Desktop wallet setup

After the MN is up and running, you need to configure the desktop wallet accordingly. Here are the steps:
1. Open the Nitrous Desktop Wallet.
2. Go to RECEIVE and create a New Address: **MN1**
3. Send **10000** N2O to **MN1**. You need to send all 10000 coins in one single transaction.
4. Wait for 15 confirmations.
5. Go to **Help -> "Debug Window - Console"**
6. Type the following command: **masternode outputs**
7. Go to  **Tools -> "Open Masternode Configuration File"**
8. Add the following entry:
```
Alias Address Privkey TxHash TxIndex
```
* Alias: **MN1**
* Address: **VPS_IP:PORT**
* Privkey: **Masternode Private Key**
* TxHash: **First value from Step 6**
* TxIndex:  **Second value from Step 6**
9. Save and close the file.
10. Go to **Masternode Tab**. If you tab is not shown, please enable it from: **Settings - Options - Wallet - Show Masternodes Tab**
11. Click **Update status** to see your node. If it is not shown, close the wallet and start it again. Make sure the wallet is unlocked.
12. Select your MN and click **Start Alias** to start it.
13. Alternatively, open **Debug Console** and type:
```
masternode start-alias MN1
```
14. Login to your VPS and check your masternode status by running the following command to confirm your MN is running:
```
nitrous-cli masternode status
```
***

## Usage:
```
nitrous-cli masternode status
nitrous-cli getinfo
nitrous-cli mnsync status
```
Also, if you want to check/start/stop **Nitrous**, run one of the following commands as **root**:

```
systemctl status Nitrous #To check if Nitrous service is running
systemctl start Nitrous #To start Nitrous service
systemctl stop Nitrous #To stop Nitrous service
systemctl is-enabled Nitrous #To check if Nitrous service is enabled on boot
```
***

## Masternode update:
In order to update your Nitrous Masternode to version 3.1.0.1, please run the following commands:
```
cd /tmp
wget -N https://github.com/zoldur/Nitrous/releases/download/v3.1.0.1/nitrous.tar.gz
tar xvzf nitrous.tar.gz
systemctl stop Nitrous
mv nitrousd nitrous-cli /usr/local/bin
systemctl start Nitrous
nitrous-cli getinfo
```
Open your desktop wallet and start the node from there.
***

## Donations

Any donation is highly appreciated

**N2O**: Ni8ncZPq1taUH8uE56spcDq3V6DSY2Nsjc
**BTC**: 3MQLEcHXVvxpmwbB811qiC1c6g21ZKa7Jh
**ETH**: 0x26B9dDa0616FE0759273D651e77Fe7dd7751E01E
**LTC**: LNZpK4rCd1JVSB3rGKTAnTkudV9So9zexB
