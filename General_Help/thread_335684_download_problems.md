---
title: "download problems"
date: 2007-01-10
forum: General Help
---

### Post by dsimpson on 2007-01-10
I did an update and then had problems trying to download programs. I tried to download SSH and related files through synaptic and got a message which said download couldn't be completed. I tried to download/install Scribus via add/remove and received similar message:

The following problems were found on your system.
W: Failed to fetch [http://archive/ubuntu/pool/main/scribus/](http://archive/ubuntu/pool/main/scribus/)
scribus 1.2.4.1dfsg-1 ubuntu i386.deb
could not connect to 127.0.0.1:8080 (127.0.0.1) -connect (111 connection refused)

I have been trying to network my 2 computers together (one connected by ethernet, the other by Belkin wireless router, and the 127.0.0.1 number I believe relates to the Belkin router, but I don't know what I could have done to make the error message i am getting. I still have internet connection on both computers and can connect from one computer to the other but not the other way around. any ideas? :confused:

---

### Post by Demon012 on 2007-01-10
Not completely sure what you have done but 127.0.0.1 is what is called a loop back address and refers to the computer you are currently using. Have you changed your network settings to point to your computer as the default gateway rather than your router (its ip should be something along the lines of: 192.168.0.1 / 192.168.1.1 or 10.0.0.1) 

Edit: Looks like it isnt this because you still have an internet connection. But 127.0.0.1 is a loopback address regardless.

Demon012

---

### Post by dsimpson on 2007-01-11
Thanks for the reply, Demon 012; the only odd thing that I noticed was a small difference when I looked in 
System/Preferences/Network Proxy  -  Proxy Configuration = Direct Internet Connection    Advanced Configuration = localhost  127.0.0.0/8  *.local  --- It is the 127.0XXX number that is causing me some wonder, don't know how it got there or if it is wrong.

Looking in System/Administration/network tools  -  location = eaglesoldier  loopback ip address = 127.0.0.1  -  unknown interface (ath0) = 192.168.2.3  -  under interface properties Belkin 54g  -  key type  =  Hexidecimal  -  configuration = DHCP                                                      

Looking in System/Administration/Networking  -  location = eaglesoldier  -  connections = Wireless Connections ath0 is active  -  under the General tab -  hostname = eaglesoldier  -  DNS = DNS Servers - 192.168.2.1  -  12.213.224.61  -  and Hosts = IP Address  -  127.0.0.1  localhost.  localdomain  localhost local  eaglesoldier

I don't know if this helps much, I have been reading my Ubuntu book and looking in the forums but still haven't found a possible solution. loking under ifconfig, everything seems ok, the addresses are the same, it says UpBroadcast is Running and Loopback is running, doesn't seem to be anything obvious unless I am missing something, which could very well be possible. Anymore ideas coming on this subject?, I would hope so. ](*,)

---

### Post by dsimpson on 2007-01-12
Hi, here again and updating my system seems to be the cause of my problems and they seem to run deeper than just synaptic and add/remove. I also seem to have lost my administrative privileges on terminal also. So now I cannot download at all, cannot do updates, even for apt-get , synaptic or add/remove. Would appreciate any help in restoring my control over download problems. I seem to be able to enter commands into terminal and it asks for my password so some function seems to still be available to me, I just need some guidance in the repair of my system.:???:

---

### Post by dsimpson on 2007-01-13
Hi I posted as download problems but am retitling to "failure to fetch" in hopes it may be more explanatory and someone out there may have a solution for me. Please check through my posts and see if there is a pattern that might explain the problem. I have internet access, sudo and password works, but problems begin when the download should take place. The error codes are all like the first post in which the archives cannot be accessed, just replace the Scribus in that post with any other software, update that is available from Ubuntu for download and it all fails whether attempted by Synaptic, Terminal, Add/Remove, or Ubuntu Update Manager. I really need help with this one, could someone please help.:confused:

---

