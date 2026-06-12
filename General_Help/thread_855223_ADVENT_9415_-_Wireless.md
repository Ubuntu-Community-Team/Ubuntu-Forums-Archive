---
title: "ADVENT 9415 - Wireless?"
date: 2008-07-10
forum: General Help
---

### Post by bastones on 2008-07-10
Hello,

I went to Network and 2 options only appeared, one saying 'Wired Connection' or something... my wireless device is Realtek RTL8187B and normally with Vista I have to press FN + F10 to activate wireless. Is there same problem in Ubuntu?

PS: I was originally told Ubuntu has native support for my wireless device and I used the acpi workarounds...

---

### Post by Gunman1982 on 2008-07-10
Open a console and execute the following commands and write the output here if you can:
'iwconfig' <- shows what your settings for wireless adapter are
'ifconfig' <- gives you info if your network device is up and running
'cat /proc/modules' <- shows which modules (something like driver) are loaded

---

### Post by bastones on 2008-07-10
iwconfig comes back with no wireless extensions for both lo and eth0 ifconfig came back with two sections (pretty much like paragraphs long) but it was really too long to write down...

---

### Post by Gunman1982 on 2008-07-10
So it seems that the right module for the wireless adapter is not loaded or 'sudo iwconfig' would give you something like this:

eth1      IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: none
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Encryption key: off   Security mode:open
          Power Management:off
          Link Quality=76/100  Signal level=-53 dBm  Noise level=-86 dBm
          Rx invalid nwid:0  Rx invalid crypt:23  Rx invalid frag:0
          Tx excessive retries:224  Invalid misc:0   Missed beacon:0

Can you give the output of 'lspci'?

PS: I am sorry but I forgot to mention the 'sudo ' in front of iwconfig/ifconfig. But I guess you did it right if it told you no wireless extensions

---

### Post by bastones on 2008-07-10
I cannot keep switching from Vista to Ubuntu... but nonetheless, most including USB and other options said Silicon Integrated Systems...

---

### Post by Gunman1982 on 2008-07-10
Mhh do you have the possibility to connect your laptop via network cable or is that not possible? Its hard to find out what you need to do when I don't have information about the system.

---

### Post by bastones on 2008-07-10
I tried connecting using Ethernet but when I go in Firefox I type in ubuntu.com for instance, it just continually says 'Waiting...' - I need to be able to use wireless and my wireless card is supported without ndiswrapper, is it something to do with ADVENT 9415 laptops?

---

### Post by Gunman1982 on 2008-07-10
I don't know since I don't have such a laptop. Can you plug in the ethernet cable again, boot up ubuntu, open a console and execute 'sudo dhclient eth0' and then try again with firefox.

---

### Post by bastones on 2008-07-10
This is getting quite annoying... but I do appreciate your help. It must be something to do with the hardware / laptop as it has worked on previous laptops I use to have with ethernet connection automatically... and as you have guessed, no it didn't work...

---

### Post by Gunman1982 on 2008-07-10
Did it give you any error messages? Do you have a router? Can you connect to it while under windows (via ethernet, not wireless)? You can try to give your laptop a fixed ip in linux. You should connect with windows start a cmd window (start->execute and then type in cmd) and there type in 'ipconfig /a' that should give you ip address, gateway and dns server, write that down. Fire up ubuntu and configure your network with these fixed values. (still ethernet)

---

### Post by bastones on 2008-07-10
didn't work... but some hope I did sudo ipconfig and it came back with as you described earlier with eth0 192.168.1.67 and I believe as I used ipconfig command in command line (vista) that's the IP I was given... I hope this can be fixed as I really do want to switch to Ubuntu completely...

---

### Post by onewithnature83 on 2008-07-20
maybe?

Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

