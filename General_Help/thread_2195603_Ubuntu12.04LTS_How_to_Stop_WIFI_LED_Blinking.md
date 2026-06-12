---
title: "Ubuntu12.04LTS How to Stop WIFI LED Blinking ?"
date: 2013-12-25
forum: General Help
---

### Post by agerpark on 2013-12-25
Hello everyone,

I'm Ubuntu 12.04 user..
My laptop system HP Elitebook 8440P and Ubuntu 12.04 LTS 64bit installation

I want to wifi LED Blinking stop..WIFI LED Blinking whenever use Network. so, i want to your advice 
My Ubuntu 12.04 don't found the Wlan.conf or iwlagn..
Don't solutions(don't found files) : [http://sumanta679.wordpress.com/2012/06/24/hp-elitebook-wifi-led-blinking-in-ubuntu/](http://sumanta679.wordpress.com/2012/06/24/hp-elitebook-wifi-led-blinking-in-ubuntu/)


test@test-HP-Elitebook-8440P:~$ uname -a
Linux test-HP-Elitebook-8440P[COLOR=#ff0000] 3.8.0[/COLOR]-34-generic #49~precise1-Ubuntu SMP Wed Nov 13 18:05:00 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

test@test-HP-Elitebook-8440P:~$ lspci -vnn | grep Network
00:19.0 Ethernet controller [0200]: Intel Corporation 82577LM Gigabit Network Connection [8086:10ea] (rev 05)
43:00.0 Network controller [0280]:[COLOR=#ff0000] **Intel Corporation Centrino Advanced-N 6200** [/COLOR][8086:4239] (rev 35)

---

### Post by mikewhatever on 2013-12-25
Can you post the output of **lspci -nnk | grep -A2 0280** to show us the module. I thought that wireless card uses **iwlwifi**, but since you've said it something's wrong with the howto, perhaps I got it wrong.

---

### Post by agerpark on 2013-12-31
I was checked for Wifi Driver iwlwifi. but each time use the internet WIFI LED continue to twinkle..
So do not have a way to stop?

when you on the Windows, WIFI Disable color red, enable color blue.
Thanks a lot.

---

### Post by tgalati4 on 2013-12-31
```
modinfo iwlwifi
```

tgalati4@Mint14-Extensa ~ $ modinfo iwlwifi | grep blink
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)

Reload the module with led_mode=3.  Otherwise, use some black tape.

---

### Post by agerpark on 2014-01-04
Thank you tgalati4

i want to know Wifi enable " blue"  or disalbe "RED".
Is there any other way?

Thank you so much

---

### Post by mikewhatever on 2014-01-04
Are you going to post the requested outputs?

---

### Post by philinux on 2014-01-04
This worked for me on 13.10
[http://jackiechen.org/2013/01/28/disable-the-blinking-wifi-led-in-ubuntu/](http://jackiechen.org/2013/01/28/disable-the-blinking-wifi-led-in-ubuntu/)

```
lspci -nnk | grep -A2 0280
02:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0083]
```

I've now got solid orange light.

I used ```
sudo nano /etc/modprobe.d/iwlwifi.conf
```and added the option, options iwlwifi led_mode=1, to the file.

---

### Post by agerpark on 2014-01-06
Hi philinux,

Your means, created new file for iwlwifi.conf?
correct?? because, i don't found file by iwlwifi.conf.. so, i can't LED blink stop.

Whatever, Can I apply Copy and paste the file to the created file?

[COLOR=#666666][FONT=Lucida Grande]# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]# microcode file installed on the system.  When removing iwlwifi, first[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]# remove the iwl?vm module and then iwlwifi.[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]remove iwlwifi[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande](/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod)[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]&& /sbin/modprobe -r mac80211[/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande][/FONT][/COLOR]
[COLOR=#666666][FONT=Lucida Grande]**options iwlwifi led_mode=1**[/FONT][/COLOR]

---

### Post by philinux on 2014-01-06
Just to be sure run this.  It will show if you have the file or not.

```
cat /etc/modprobe.d/iwlwifi.conf
```

---

