# Configuration_WC
## wireless attack - ethical hacking

Before starting the configuration phase, the first thing to do is to be able to configure the wifi card adequately.

The tests were carried out with an external wifi card of the `ALFA NETWORKS AWUS036NH` type using `VMWARE` as a virtualization platform.

`NB:` virtualization does not support PCI cards.

```bash
iwconfig
```
output 
```terminal
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11  ESSID:"4G_WIFI_GLISH"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: 98:A9:42:44:84:F8   
          Bit Rate=72.2 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-40 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:6   Missed beacon:0
```
### my dBm is 22 we can increase it to 30. 
```bash
iwconfig wlan0 txpower 30
```

```bash 
sudo airmon-ng start wlan0
```
output
```
Found 2 processes that could cause trouble.
Kill them using 'airmon-ng check kill' before putting
the card in monitor mode, they will interfere by changing channels
and sometimes putting the interface back in managed mode

    PID Name
   1110 NetworkManager
   1135 wpa_supplicant

PHY	Interface	Driver		Chipset

phy0	wlan0		iwlwifi		Intel Corporation Wireless 7260 (rev 6b)
		(mac80211 monitor mode vif enabled for [phy0]wlan0 on [phy0]wlan0mon)
		(mac80211 station mode vif disabled for [phy0]wlan0)
```
our card is in `wlan0mon` monitoring mode so we can use it to carry out attacks etc.

sudo iwconfig wlan0mon mode managed