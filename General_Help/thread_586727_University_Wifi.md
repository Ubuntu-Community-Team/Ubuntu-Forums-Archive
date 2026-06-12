---
title: "University Wifi"
date: 2007-10-22
forum: General Help
---

### Post by KillerZ on 2007-10-22
I just installed Gutsy and I am trying to get it to connect to my schools wireless network. I original posted about a week ago when I had Feisty installed for help here is my original [_post_]("http://ubuntuforums.org/showthread.php?t=571906"). I tried to get it to work but I couldn't so I went back to windoze to get my wireless internet but I prefer Ubuntu so I was wondering if I could get some more help trying to connect because I am new at this and not very good at using the terminal. [_Here_]("http://campus.upei.ca/computerservices/facilities/wireless/configuration_vista") is my university's directions for connecting vista to the network using SecureW2 but there is no Linux version of SecureW2. :confused:

---

### Post by ddrichardson on 2007-10-22
You may have some trouble with this. SecureW2 is an EAP implementation for which I've only seen one guide in Ubuntu [here]("https://help.ubuntu.com/community/WifiDocs/Device/CiscoCB21AG").

I would speak with your College IT department first because having gone to the trouble of securing their network they most likely have a policy in place that you could end up in bother for circumventing. They may also be able to help you out.

---

### Post by KillerZ on 2007-10-22
Ya my schools network does have a policy but using Linux does not void it I don't think. the policy is about not doing illegal things(downloading music...etc), interfering with the network by bypassing security or spreading viruses. But my schools IT department only supports windows actually only XP they only have basic vista support lol. there is a [_mac_]("http://campus.upei.ca/computerservices/facilities/wireless/mac_details/") guide also that doesn't use SecureW2 but it was wrote by a student. I am still new at this so i am not that familiar with the terminal I can use it if I am told what to type lol. :confused:

---

### Post by hugomeeuwes on 2007-11-02
U can use wpa_supplicant instead of SecureW2.
It also works for wired connections.

The settings depend on the university. Some use certificates for SecureW2. Wpa_supplicant does support them, just google on how to add them.

For me (Erasmus University Rotterdam with wired connection), the settings are:

/etc/wpa_cupplicant.conf:
(location can differ, just make sure it is referred to correctly in the interfaces file)

```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=0 #I've got a wired connection and dont't want to look for hotspots

network={
key_mgmt=IEEE8021X
eap=TTLS
identity="000000aa@eur.nl"
anonymous_identity ="000000aa@eur.nl"
password="pass" 
phase2="auth=PAP"
}
```

and in my /etc/network/interfaces it looks like (just add the pre-up and down):

```
auto eth0
iface eth0 inet dhcp
pre-up wpa_supplicant -Bw -Dwired -ieth0 -c/etc/wpa_supplicant.conf
pre-down killall -q wpa_supplicant
```

if you're connection is wifi, -Dwired should be -Dwext

---

### Post by jljansen on 2008-01-15
Dear Hugo Meeuwes,

I tried your solution for wireless authentication with a laptop on the EUR network! I don't get it working!

I use the following in my wpa_supplicant file
```
ctrl_interface=/var/run/wpa_supplicant
ap_scan=1 

network={
ssid="eduroam"
scan_ssid=1
key_mgmt=IEEE8021X
eap=TTLS
identity="000000aa@eur.nl"
password="pass" 
phase2="auth=PAP"
}
```

to start it I use
```
 sudo wpa_supplicant -i wlan0 -D wext -c /etc/wpa_supplicant.conf
```

What I'm I doing wrong? Does the EUR require additional certificates?

Hope you can help me on my way! Thx in advance...

Edit:
Unfortunately I have a RaLink RT2561/RT61 rev B 802.11g so the rt61pci drivers were causing trouble on eduroam-guest! This one is working! But I'm still curious about working wpa_supplicant.conf file for the EUR! So does anybody has one working?

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

