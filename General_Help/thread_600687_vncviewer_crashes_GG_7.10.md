---
title: "vncviewer crashes GG 7.10"
date: 2007-11-02
forum: General Help
---

### Post by mx119 on 2007-11-02
I just upgraded to Gutsy Gibbon and I use vpnclient (with the new patches for the updated kernel, again) to connect to work. 

As soon as I start vncviewer connecting to any of the machines at work(either linux or solaris) my entire system locks up. It is completely unresponsive to any keyboard or mouse input, and ctrl-alt-f[1-9] does nothing. it is not random and happens ~1s after the vnc screen appears ( I can actually see my work desktop). 

The same setup (minus the vpnclient module update) has been working fine on 7.04.  

Since I did an upgrade I tried a fresh install of the OS on a separate partition and get the same thing every time. 

I did upgrade the hardware 1 week before 7.10, however,  vpn/vnc was working with 7.04 fine after the hw update.

Has anyone seen this, or have any suggestions. I am getting to the point where I am either going to have to go back to FF or change to another distro so I can work from home. 

thanks

---

### Post by drwho on 2007-11-03
I have the exact same problem. I used the Cisco 4.8.1.*** vpnclient. Both krdc and xtightvncviewer cause a freeze. The only response from the system is the blinking caps lock and scroll lock lights.

Any help?

7.10 (x86) on Dell Vostro 1500.

---

### Post by mx119 on 2007-11-12
Update:

I could not get vpnclient to work with vncviewer. 

I am now successfully using (k)vpnc, which is a better solution for me since it does not require loading a kernel module. I had initially tried kvpnc as was suggested on the ubuntu forums, but had problems. It turns out all I had to do was setup the session manually as "pcf import" did not work for me. I got all the information from the pcf and used [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)
to decrypt the password. 

vncviewer works fine with vpnc

---

### Post by drwho on 2007-11-18
Unfortunately, I have to use some Cisco supported features. VPNC is not an option. Maybe a fix will appear soon.

---

### Post by fragos on 2007-11-18
Using the "Remote Desktop" preferences and vncviewer {IP address} works correctly between a two systems, one is 7.10 and the other 7.04.  The 7.10 is cabled into a wireless router and the 7.04 is a WiFi connection.

---

### Post by GaryZ on 2007-12-29
I have exactly the same problem with vpnclient-linux-x86_64-4.8.01.0640-k9 and 7.10 on a Dell Precision M6300.  My caps and scroll lock lights flash, and the system is unresponsive shortly after remote connection to a WinXP machine over the VPN.  I've tried tsclient with RDP, vncviewer, and using FireFox to connect to UltraVNC javaviewer, all with the same result.

Thanks.

---

### Post by ShinShin on 2008-01-04
Same here :(

I'm not on v4.8.01.0640-k9 yet. I'm using v4.8.00.0490-k9 and patched with [http://tuxx-home.at/archives/2007/05/29/T16_34_26/](http://tuxx-home.at/archives/2007/05/29/T16_34_26/) to get it working with linux 2.6.22

I may just upgrade and see if that helps but otherwise is there anything I can do to diagnose the problem?

Thanks

---

### Post by cgarre on 2008-01-22
I am also having the same problem. Am on GG , using cisco vpn. 
rdekstop or tsclient all dont work , the kernel panics in about 1-2 seconds of showing the remote desktop login screen. sometimes it panics before the whole screen appears and sometimes it panics when trying to login. panic = capslock and scroll lock blink and everything hangs. help please .....

---

### Post by cgarre on 2008-01-23
Here is the solution, after a long struggle

1. Dont use cisco vpn, even if you were using it in windows/ your company runs cisco vpn. No need to use cisco VPN client in any circumstances (atleast 90% of the cases probably, i cant be 100% sure), but i didnt have to use for my company ... 
2. Follow steps in [http://www.spiration.co.uk/post/1293](http://www.spiration.co.uk/post/1293)
3. No need to worry about the decoding part, you can use this website to easily decode the encrypted group password [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)
4. Have a default.conf file in /etc/vpnc make sure you are logged in as root (using su root) 
5. If its first time, then copy example.conf, and get values from your .pcf file. Remember your windows machine where you installed and were using cisco vpn will have .pcf file that will have the details. 

!Description=Your Company 
!Host=xxx.xxx.xxx.xxx
!AuthType=1
!GroupName=yourcompanyvpn
!GroupPwd=
!enc_GroupPwd=ABAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA

you should worry about only these, i have changed the details to protect information. 

the enc_GroupPwd is to be used to find the real grouppwd, from the website given below.

then replace these in the file (create if you dont have) default.conf 
IPSec gateway xxx.xxx.xxx.xxx
IPSec ID yourcompanyvpn
IPSec secret decodedGroupPwd
Xauth username myUserName

5. Now start vpnc using    
     vpnc
     
     Here it will ask you for the password, thats it give the password. 


Usually this should work for most .pcf files, there might be some complex pcf files, which might need better study. 

Once vpnc is running it will be in the background. 
Now you can ping to one of your office computers, it should work. 

6. Use rdesktop or tsclient to connect via RDP to windows computers in your office network ! 


Thats it , its a breeze, i struggled, with kernel panic for almost 6 hours, and i was thinking it was rdesktop that was at fault, then slowly i realized it was cisco vpn that was killing ubuntu 7.10. 

ps Kernel Panic = Blinking Caps Lock and Scroll Lock and everything hangs , you have to power down, thats it.
Enjoy linux,,,

---

