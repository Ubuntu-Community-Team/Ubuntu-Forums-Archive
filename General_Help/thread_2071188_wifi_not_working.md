---
title: "wifi not working"
date: 2012-10-14
forum: General Help
---

### Post by langmarp on 2012-10-14
os: xubuntu 12.04 (updated)
laptop: HP Compaq nc6120

After install wifi worked just fine, but after a few days wifi hardware has been blocked. Same happened with Ubuntu 12.04. Ethernet works well.

this wont solve the problem:
```
sudo rfkill ublock all
```

Any idea what to do? Thank you!

please, see the details here:
```
csicsi@csicsi-HP:~$ sudo iwconfig 
lo        no wireless extensions. 

eth1      IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Encryption key:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

eth0      no wireless extensions. 

csicsi@csicsi-HP:~$ rfkill list 
0: hp-wifi: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: yes 
1: phy0: Wireless LAN 
	Soft blocked: yes 
	Hard blocked: yes 
csicsi@csicsi-HP:~$ sudo iwlist ethl scanning 
ethl      Interface doesn't support scanning. 

```

---

### Post by Yrralhann on 2012-10-14
Have you recently installed any firewall software... like firestarter for example? Firestarter only seems to work with either wifi or ethernet, you have to reconfigure it when you want to switch....... try turning off your firewall(if this is the case) and see if wifi is working then.

I get the same results with my firewall running, unless i reconfigure it for wifi.

---

### Post by langmarp on 2012-10-14
no additional firewall has been installed...

---

### Post by cariboo on 2012-10-14
A firewall is included by default, when you do a Linux installation. To check if you have it enabled, open a terminal and type the following command:

```
sudo ufw status
```

if the firewall isn't enabled, the output of the above command should look like this:

```
sudo ufw status
[sudo] password for cariboo: 
Status: inactive
```

---

### Post by Yrralhann on 2012-10-14
I'm guessing you rebooted after doing rfkill unblock?

It's saying your wifi is hard blocked though, if that's correct, it suggests that it has been physically turned off on your laptop..... does your laptop have a touch panel to let you eneable and disable certain features? If your panel shows your wifi as on, and ubuntu is telling you it's hard blocked.... It might mean there could be some kind of hardware issue.... try toggling it on and off a few times on your laptops panel thingy and see if that does anything?

Edit: Looking at your laptop, it appears you do have a wifi toggle button(not a touch panel, same thing though), try jamming that button a few times, it may be stuck, or not making good contact or something.

---

### Post by langmarp on 2012-10-14
cariboo907, yes, it is inactive
Yrralhann, yes, my laptop has a wifi button, but the button has been disabled too, it isn't reactive any more, but this isn't because of a physical damage.

I am pretty sure, that the issue is caused by a software issue...
I know, that it sounds weird that the wifi hard block is caused by a software, but I am certain, that this is the case... It worked fine for a while both under Xubuntu and Ubuntu 12.04 before being hard blocked.

Thanks for both of you!!!

---

### Post by Yrralhann on 2012-10-14
> **langmarp said:**
> 

I am pretty sure, that the issue is caused by a software issue...

It's possible, but i can reproduce your rfkill list simply by toggling off wifi on my laptop panel 

Wifi switch on
```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: acer-wireless: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Wifi switch off
```
rfkill list
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
```
You mentioned about your wifi button no longer working? That immediatly causes me to suspect that the button may be the problem, or did you mean it was intentionally disabled by disconnecting it from the motherboard or something?

Are you dualbooting anything else on this system? If so, does your wifi work ok in other OS?

---

### Post by danelwillis on 2012-10-14
Had this problem myself on Toshiba NB200, the problem was software, and it took a full year and a have to fix this. I had to install the original OS created by your Computers manufacturer. Because it was a netbook I had no disk drive, I had to buy the usb  and reinstall xp and the specific drivers. Then had to make sure the wi-fi was turned on both software and hardware. Then re-installed kUbuntu. :)

---

### Post by langmarp on 2012-10-15
Could I turn on by wifi somehow with rfkill?

The button has been disabled by the OS, but physically its working fine.

I just dont get this issue...

Thanks for your help!

---

### Post by danelwillis on 2012-10-18
This is 100% OS software problem so the only solution is to resort back to the original OS with the original Software and Drivers. That seems to be the only way to solve this problem.

---

