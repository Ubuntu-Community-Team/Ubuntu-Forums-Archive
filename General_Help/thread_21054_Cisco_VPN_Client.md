---
title: "Cisco VPN Client???"
date: 2005-03-20
forum: General Help
---

### Post by hemps on 2005-03-20
Great work on this clean amazing distro. Has anyone managed to get Cisco VPN Client to work with this latest release? I have the source ,gcc and the Cisco client, and have been able to install it  on FC3, Mandrake, Suse, and the prior Ubuntu version, not able to get it working with Hoary yet. Has anyone managed to get this working?

---

### Post by ACK!! on 2005-03-20
[QUOTE=hemps]Great work on this clean amazing distro. Has anyone managed to get Cisco VPN Client to work with this latest release? I have the source ,gcc and the Cisco client, and have been able to install it  on FC3, Mandrake, Suse, and the prior Ubuntu version, not able to get it working with Hoary yet. Has anyone managed to get this working?[/QUOTE]

Yep, I did.  

You know the patch right?  

This is the already patched now infamous interceptor.c  

[http://www.ces.clemson.edu/linux/interceptor.c](http://www.ces.clemson.edu/linux/interceptor.c)

Now deal is the wonderful gnome vpn tool did not work.   :( 

Reason is for me I have this prompt after username and pass that asks me if I am really sure I want to enter this private network under threat of blah ...blah ... and oh yeah more blah.  

The gnome vpn client did not work for this and cisco vpn alternatives like vpnc barfed hard even after hard tinkering.  So for me it was cisco vpn from the command line or nothing.

Anyway, cisco vpn does NOT seem to put a link in the rc2.d directory so I had to make one to start the service.

Yes the below script is no big deal and I could make it better and all that but ....


#!/bin/sh
# I am Johnathan Bailes and I endorse this really short nautilus script.

gnome-terminal -t "Cisco VPN Connect" -x vpnclient connect <your-profile>

---

### Post by hemps on 2005-03-20
Thanks ACK,
I will give that a try, I didnt know about the patch.
Cheers
Hemps

---

### Post by hemps on 2005-03-20
Maybe Im doing something wrong?
 I applied the patch with patch -p0 < patch.txt . Said that it applied correctly. I apt'ed the kernel-source and untarred the .bz2 file it created in the /usr/src/ directory. I then ran the ./vpn_instal answered the questions and ponted to the /usr.src/linux-source-2.6.10 directory. It runs through many, many pages of errors etc and finally give me a 
include/linux/fs.h:807: error: storage size of `s_vfs_rename_sem' isn't known
include/linux/skbuff.h:146: error: storage size of `frags' isn't known
include/linux/seq_file.h:21: error: storage size of `sem' isn't known
include/net/neighbour.h:140: error: storage size of `arp_queue' isn't known
include/net/neighbour.h:182: error: storage size of `parms' isn't known
include/net/neighbour.h:191: error: storage size of `proxy_queue' isn't known
include/net/sock.h:205: error: storage size of `sk_receive_queue' isn't known
include/net/sock.h:207: error: storage size of `sk_write_queue' isn't known
include/net/sock.h:231: error: storage size of `sk_error_queue' isn't known
include/net/sock.h:241: error: storage size of `sk_peercred' isn't known
include/net/sock.h:249: error: storage size of `sk_stamp' isn't known
include/linux/in6.h:56: error: storage size of `sin6_addr' isn't known
include/linux/ip.h:143: error: storage size of `fl' isn't known
make[2]: *** [/root/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/root/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Error. and thats as far as I get.

Ryan

---

### Post by ACK!! on 2005-03-20
[QUOTE=hemps]Maybe Im doing something wrong?
 I applied the patch with patch -p0 < patch.txt . Said that it applied correctly. I apt'ed the kernel-source and untarred the .bz2 file it created in the /usr/src/ directory. I then ran the ./vpn_instal answered the questions and ponted to the /usr.src/linux-source-2.6.10 directory. It runs through many, many pages of errors etc and finally give me a 
.....

make[2]: *** [/root/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/root/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-source-2.6.10'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Error. and thats as far as I get.

Ryan[/QUOTE]

Yep, got that too.  First the file I linked to should be the fully double patched good to god file so you did not have to do the patch.  But the patch will work and worked for me back in the day.

So what about the errors.  The Kernel Source stuff is not good enough.  Sounds crazy right?  

I know.  

Deal is that you need a linux-headers package as well.  No, it does not make perfect sense to me either.  

I cannot remember if I had to leave that directory untarred in the kernel source section or delete it and point the install at where the linux-headers package puts stuff or what.  

I think the second is what I did but like I said I cannot remember.  

linux-headers-2.6.10-4-686
Header files related to Linux kernel version 2.6.10 was the package in Synaptic I chose.

yes, it all depends on the kernel you are running.  

Installed files indicates it puts everything in /usr/src/linux-headers-2.6.10-4-686 and that it left a symlink from /usr/src/linux to /usr/src/linux-headers-2.6.10-4-686.

This leads me to believe I whacked the bz2 untarred kernel source I created and just used the linux-headers package for the compilation of Cisco VpnClient.

Btw, good luck.

---

### Post by hemps on 2005-03-20
Whoooo-Hoo
 :-D 
ACK!!
You ROCK,got it working using the linux-headers.

Thank you very much
Hemps

---

### Post by ACK!! on 2005-03-20
[QUOTE=hemps]Whoooo-Hoo
 :-D 
ACK!!
You ROCK,got it working using the linux-headers.

Thank you very much
Hemps[/QUOTE]

If your vpn does not do the yes/no authorization prompt after username and password challenge then you should try out the gnome vpn tools.  vpn-applet is the name of the package.  

I cannot remember if I had to add a repo to get it or it is available in the regular ubuntu channels.

If that does not work for you try my little nautilus script above.  Throw it in your ~/.gnome2/nautilus-scripts dir and it should appear when you right click your desktop under the scripts subdir.  

Btw, glad to help.

---

### Post by venkatu on 2005-04-13
just posted a comment on the bugzilla ([https://bugzilla.ubuntu.com/show_bug.cgi?id=7968](https://bugzilla.ubuntu.com/show_bug.cgi?id=7968)). it  has a couple of workarounds to prevent vpnclient from freezing hoary's kernel.

i am too lazy to compare the patch above to the patch on the linked page, they may be same though :)

---

### Post by Ramza500 on 2005-04-13
Hey guys,

I'm using the vpnclient 4.6.02.0030-k9 and am having trouble having it read my profile.

I copied the .pcf directly from the Windows version of it and tried vpnclient connect my.pcf and it says "The specified profile could not be read."

So then I downloaded the manual for the vpnclient and went through re-writing the whole thing to use only the commands listed in the manual.

Still the same problem, it can't even read the sample.  Anyone know why this is happening?

Thanks

---

### Post by djjazzy on 2005-04-14
Having issues installin Cisco client 4.6.02 and am a fairly stupid noob, loving Hoary tho. I get this gag:

Is the above correct [y]

Making module
make -C /usr/src/linux-headers-2.6.10-5-686 SUBDIRS=/home/woodman/Download/vpnclient modules
/usr/src/linux-headers-2.6.10-5-686/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-5-686/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /home/woodman/Download/vpnclient/linuxcniapi.o
/bin/sh: gcc: command not found
make[2]: *** [/home/woodman/Download/vpnclient/linuxcniapi.o] Error 127
make[1]: *** [_module_/home/woodman/Download/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Synaptic shows I have gcc-3.3-base installed. I'm lost, can anyone help me out?

---

### Post by luvdemheels on 2005-04-14
I was getting that yesterday and then installed vpnc and it worked perfect and is very easy (I have a cisco pix that I connected to). vpnc works in place of the cisco vpn client.

In case you are wondering, I used synpatic to install vpnc.

---

### Post by Ramza500 on 2005-04-14
[QUOTE=djjazzy]Having issues installin Cisco client 4.6.02 and am a fairly stupid noob, loving Hoary tho. I get this gag:

Is the above correct [y]

Making module
make -C /usr/src/linux-headers-2.6.10-5-686 SUBDIRS=/home/woodman/Download/vpnclient modules
/usr/src/linux-headers-2.6.10-5-686/scripts/gcc-version.sh: line 11: gcc: command not found
/usr/src/linux-headers-2.6.10-5-686/scripts/gcc-version.sh: line 12: gcc: command not found
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686'
  CC [M]  /home/woodman/Download/vpnclient/linuxcniapi.o
/bin/sh: gcc: command not found
make[2]: *** [/home/woodman/Download/vpnclient/linuxcniapi.o] Error 127
make[1]: *** [_module_/home/woodman/Download/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Synaptic shows I have gcc-3.3-base installed. I'm lost, can anyone help me out?[/QUOTE]

This may seem stupid, but were you root?

---

### Post by djjazzy on 2005-04-14
Yeah I was root, but when I do whereis gcc as user or root it's not located.

---

### Post by Ramza500 on 2005-04-14
At the time I installed the client I had the following gcc packages installed:
gcc
gcc-3.3
gcc-3.3-base
gcc-3.4
gcc-3.4-base
gcc-4.0-base
libgcc1

However, when I do a gcc --help to check which version it refers to, it refers to 3.3.  Maybe you can see if installing those packages will help.

---

### Post by djjazzy on 2005-04-15
I installed the gcc stuff in your list Ramza and that allowed the client install to run. Thanks for the assist. Now I have a new problem and one that I have seen before on other machines. When I run /etc/init.d/vpnclient_init start I get:

Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.10-5-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

Had a dig on this output, turned up very little. I had a Gentoo machine also 2.6 kernel that gave the same error. This is the only thing holding me back from dumping m$ for good. Can anyone give me the skinny? Thx.........

---

### Post by djjazzy on 2005-04-15
BTW, I did want to mention that I tried vpnc (perfectly willing to take the easy way out) but it doesn't seem to support Radius authentication against 2k3 domain accounts which required on my office network.

---

### Post by venkatu on 2005-04-15
[QUOTE=djjazzy]I installed the gcc stuff in your list Ramza and that allowed the client install to run. Thanks for the assist. Now I have a new problem and one that I have seen before on other machines. When I run /etc/init.d/vpnclient_init start I get:

Starting /opt/cisco-vpnclient/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.10-5-386/CiscoVPN/cisco_ipsec.ko': -1 Invalid module format
Failed (insmod)

Had a dig on this output, turned up very little. I had a Gentoo machine also 2.6 kernel that gave the same error. This is the only thing holding me back from dumping m$ for good. Can anyone give me the skinny? Thx.........[/QUOTE]

to all those trying to compile this module, here are a couple of pointers:

get all the build tools using:
```
sudo apt-get install build-essential
```
this will install the compiler suite and other build tools.

get the "appropriate" kernel headers:
```
uname -r
```
will list the kernel version that you're running. go to synaptic and pull the appropriate header in. i think apt-getting linux-headers-<386/686> would pull in appropriate headers if you had installed the kernel via linux-<386/686> virtual package, i'm not sure. the module version mismatch happens when you compile a module against a different kenel-headers that doesn't match with the one that you're running.

on gentoo, you need to mke sure you have /usr/src/linux symlink pointing to the appropriate kernel source directory (matching that with the kernel that you're running).

---

### Post by djjazzy on 2005-04-15
Your advice worked Venkatu, many thanks...............Jeff

---

### Post by emmet on 2005-04-22
No joy here...

```
Making module
make -C /lib/modules/2.6.10-5-686-smp/build SUBDIRS=/home/efletcher/downloads/source/vpn_client 4.6/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.10-5-686-smp'
make[1]: *** No rule to make target `4.6/vpnclient'.  Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.10-5-686-smp'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".
```

It appears to have just barfed straight-off without thinking about it.

Any clues?

Thanks

Emmet

---

### Post by Ramza500 on 2005-04-22
Look up to make sure you have all the gcc modules installed and that you are root.

---

### Post by hemps on 2005-04-26
For All you Cisco Client Users out there, here is a Step by Step guide on how to install it on Ubuntu 5.04
 :) 

1. Mine was a fersh install
2. Place your latest Cisco Client in your home directory.
3. Do a ```
sudo apt-get install build-essential
``` 
4. Do a ```
sudo apt-get install gcc
``` 
5. Do a uname -r  to find the correct kernel-headers for your build.
6. Use synaptic to search and install the correct kernel-HEADERS, not source.
7. Untar your Cisco Client, go to the vpnclient folder and do a ```
sudo sh vpn_install
``` 
8. Answer all questions, the defaults worked for me.
9. make sure you start the vpn sub-system with
```
sudo /etc/init.d/vpnclient_init start
``` 
10. Copy your .pcf profile to the ```
sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles
```.
11. Do a vpnclient connect <your profile> (without the .pcf extention)
12. Hope this helps.

Hemps 
:)

---

### Post by irwand on 2005-05-06
I was banging my head against the wall for a while there, because it didn't work even after I used the patched interceptor.c. I could VPN just fine, but then the only thing I could do was pinging machines. If I launch web browser to view some html from internal sites, it didn't work. It turned out that my problem is the network driver. The tg3 driver, that controls broadcom NIC, doesn't work properly with Cisco VPN, as documented in Release Notes for Cisco VPN: [http://www.cisco.com/en/US/products/sw/secursw/ps2308/prod_release_note09186a00802d398a.html](http://www.cisco.com/en/US/products/sw/secursw/ps2308/prod_release_note09186a00802d398a.html). When I switched to use a different NIC, everything works.

---

### Post by TrevorNC on 2005-05-10
[QUOTE=hemps]For All you Cisco Client Users out there, here is a Step by Step guide on how to install it on Ubuntu 5.04
 :) 

1. Mine was a fersh install
2. Place your latest Cisco Client in your home directory.
3. Do a ```
sudo apt-get install build-essential
``` 
4. Do a ```
sudo apt-get install gcc
``` 
5. Do a uname -r  to find the correct kernel-headers for your build.
6. Use synaptic to search and install the correct kernel-HEADERS, not source.
7. Untar your Cisco Client, go to the vpnclient folder and do a ```
sudo sh vpn_install
``` 
8. Answer all questions, the defaults worked for me.
9. make sure you start the vpn sub-system with
```
sudo /etc/init.d/vpnclient_init start
``` 
10. Copy your .pcf profile to the ```
sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles
```.
11. Do a vpnclient connect <your profile> (without the .pcf extention)
12. Hope this helps.

Hemps 
:)[/QUOTE]
 Hemps,

Thank you for you complete list on how to get the cisco vpnclient up and running. The only issues that I had were:

Step 10. Copy your .pcf file. My installation was expecting me to place the pcf file in /etc/CiscoSystemsVPNClient/Profiles/

Also, once it was copied to this location I had to issue the following command to allow read access to the file.

sudo chmod 744 <your>.pcf

The location of the config file seems to be contained in the config.h file, for example:

>grep CiscoSystemsVPNClient *
config.h:#define UNITY_CONFIG_PATH "/etc/CiscoSystemsVPNClient"

---

### Post by super-user on 2005-05-13
Hi!

I'm trying to install this Cisco client. I have patched the interceptor.c file and so on. Have all packages installed (build-essential, gcc, g++...). I have downloaded the kernel headers and sources for my Duron (linux-image-2.6.10-k7...). My "vpnclient" dir is in "/root/HU Berlin/vpnclient". When I start "./vpn_install" the following shows:

```

Making module
make -C /usr/src/linux-headers-2.6.10-5-k7 SUBDIRS=/root/HU VPN/vpnclient modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.10-5-k7«
make[1]: *** Keine Regel, um »VPN/vpnclient« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.10-5-k7«
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".

```

This shows up, when I enter the linux-headers directory. When I enter the linux source dir, as asked for, this happens:

```

aking module
make -C /usr/src/linux-source-2.6.10 SUBDIRS=/root/HU VPN/vpnclient modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-source-2.6.10«
make[1]: *** Keine Regel, um »VPN/vpnclient« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis »/usr/src/linux-source-2.6.10«
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".

```

Unfortunateley I'm running out of my latin... Does anyone know an answer?

Daniel

---

### Post by nascent16 on 2005-05-18
[QUOTE=Ramza500]Hey guys,

I'm using the vpnclient 4.6.02.0030-k9 and am having trouble having it read my profile.

I copied the .pcf directly from the Windows version of it and tried vpnclient connect my.pcf and it says "The specified profile could not be read."

So then I downloaded the manual for the vpnclient and went through re-writing the whole thing to use only the commands listed in the manual.

Still the same problem, it can't even read the sample.  Anyone know why this is happening?

Thanks[/QUOTE]

Make sure that you don't put .pcf in your command.

IE. 

vpnclient connect sample

--NOT--
vpnclient connect sample.pcf

Perhaps that will help.

Justin

---

### Post by lildude on 2005-05-20
[QUOTE=super-user]Hi!

I'm trying to install this Cisco client. I have patched the interceptor.c file and so on. Have all packages installed (build-essential, gcc, g++...). I have downloaded the kernel headers and sources for my Duron (linux-image-2.6.10-k7...). My "vpnclient" dir is in "/root/HU Berlin/vpnclient". When I start "./vpn_install" the following shows:

```

Making module
make -C /usr/src/linux-headers-2.6.10-5-k7 SUBDIRS=/root/HU VPN/vpnclient modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-headers-2.6.10-5-k7«
make[1]: *** Keine Regel, um »VPN/vpnclient« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis »/usr/src/linux-headers-2.6.10-5-k7«
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".

```

This shows up, when I enter the linux-headers directory. When I enter the linux source dir, as asked for, this happens:

```

aking module
make -C /usr/src/linux-source-2.6.10 SUBDIRS=/root/HU VPN/vpnclient modules
make[1]: Gehe in Verzeichnis »/usr/src/linux-source-2.6.10«
make[1]: *** Keine Regel, um »VPN/vpnclient« zu erstellen.  Schluss.
make[1]: Verlasse Verzeichnis »/usr/src/linux-source-2.6.10«
make: *** [default] Fehler 2
Failed to make module "cisco_ipsec.ko".

```

Unfortunateley I'm running out of my latin... Does anyone know an answer?

Daniel[/QUOTE]


Hi Daniel

Unfortunately, your errors don't give much info as to why this is going wrong. (I don't speak german, but google helped :-))

Maybe the following tips may help:

1.  Try extracting the vpnclient source into a directory that has no spaces, eg [FONT=Courier New]*/root/HUVPN/vpnclient*[/FONT]

2.  Ensure you are using gcc 3.x and not 4.0.  ([FONT=Courier New]*ls -l /usr/bin/gcc*[/FONT]).  If it points to gcc-4.0, change the symlink to point to gcc-3.x

You didn't state which version of vpnclient or gcc you were using, but I had problems with gcc 4.0 and vpnclient 4.6.00.0045 with kernel 2.6.10-5. 

3.  When prompted for the directory containing the sources, it should automatically detect something like [FONT=Courier New]*/lib/modules/2.6.10-5-686/build*[/FONT]. Provided you've installed the headers for the kernel you are running, this dir should point to the headers.

4. Don't forget to run vpn_install as root or via sudo

HTH

---

### Post by fhennies on 2005-05-20
I seem to have a similar problem as irwand, some services work (ssh, ping), others dont (scp, http). So I have to change NIC driver, i guess. I am quite experienced in Linux, but still to fresh to know how to change the driver used for my NIC. Can anyone help?

[QUOTE=irwand]I was banging my head against the wall for a while there, because it didn't work even after I used the patched interceptor.c. I could VPN just fine, but then the only thing I could do was pinging machines. If I launch web browser to view some html from internal sites, it didn't work. It turned out that my problem is the network driver. The tg3 driver, that controls broadcom NIC, doesn't work properly with Cisco VPN, as documented in Release Notes for Cisco VPN: [http://www.cisco.com/en/US/products/sw/secursw/ps2308/prod_release_note09186a00802d398a.html](http://www.cisco.com/en/US/products/sw/secursw/ps2308/prod_release_note09186a00802d398a.html). When I switched to use a different NIC, everything works.[/QUOTE]

---

### Post by fhennies on 2005-05-20
I have solved my problem, could have searched before posting   :? 

Instead you get the solution that worked with me.

Cite from [http://www.rz.uni-saarland.de/services/netz/vpn/vpn.htm](http://www.rz.uni-saarland.de/services/netz/vpn/vpn.htm)

----

After making a VPN Client connection with Linux VPN client, some traffic types no longer work.
Specifically applications that send large packets like SMTP, HTTP, and SSH.
Conditions
The 2.6.4 Kernel enabled a feature of certain ethernet cards that discards
packets larger than the configured MTU. Since the VPN Client lowers the MTU
visible to the applications in order to add it's overhead without exceeding
the original MTU, the resulting packets are bigger than the newly configured
MTU. Therefore the card throws out the large encrypted packets.

This can easily be tested with a ping.
ping -s 500 x.x.x.x should pass
ping -s 2600 x.x.x.x should fail

Workarounds
If an lsmod shows that the "e100" driver is in use for the network card, it
can be replaced with the "eepro100" driver.

ifdown eth0
rmmod e100
modprobe eepro100
ifup eth0

----

---

### Post by dannemil on 2005-07-23
A great big tip of the hat. After an hour of frustration, I followed your directions and it worked! :) 

[QUOTE=hemps]For All you Cisco Client Users out there, here is a Step by Step guide on how to install it on Ubuntu 5.04
 :) 

1. Mine was a fersh install
2. Place your latest Cisco Client in your home directory.
3. Do a ```
sudo apt-get install build-essential
``` 
4. Do a ```
sudo apt-get install gcc
``` 
5. Do a uname -r  to find the correct kernel-headers for your build.
6. Use synaptic to search and install the correct kernel-HEADERS, not source.
7. Untar your Cisco Client, go to the vpnclient folder and do a ```
sudo sh vpn_install
``` 
8. Answer all questions, the defaults worked for me.
9. make sure you start the vpn sub-system with
```
sudo /etc/init.d/vpnclient_init start
``` 
10. Copy your .pcf profile to the ```
sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles
```.
11. Do a vpnclient connect <your profile> (without the .pcf extention)
12. Hope this helps.

Hemps 
:)[/QUOTE]

---

### Post by diffuser78 on 2005-07-24
[QUOTE=hemps]For All you Cisco Client Users out there, here is a Step by Step guide on how to install it on Ubuntu 5.04
 :) 

1. Mine was a fersh install
2. Place your latest Cisco Client in your home directory.
3. Do a ```
sudo apt-get install build-essential
``` 
4. Do a ```
sudo apt-get install gcc
``` 
5. Do a uname -r  to find the correct kernel-headers for your build.
6. Use synaptic to search and install the correct kernel-HEADERS, not source.
7. Untar your Cisco Client, go to the vpnclient folder and do a ```
sudo sh vpn_install
``` 
8. Answer all questions, the defaults worked for me.
9. make sure you start the vpn sub-system with
```
sudo /etc/init.d/vpnclient_init start
``` 
10. Copy your .pcf profile to the ```
sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles
```.
11. Do a vpnclient connect <your profile> (without the .pcf extention)
12. Hope this helps.

Hemps 
:)[/QUOTE]


I get the following error when I did what u said as aboveMaking module

make -C /usr/include/linux SUBDIRS=/home/%user%/Store/vpnclient modules
make[1]: Entering directory `/usr/include/linux'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/usr/include/linux'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Can u help further

---

### Post by diffuser78 on 2005-07-24
[QUOTE=hemps]For All you Cisco Client Users out there, here is a Step by Step guide on how to install it on Ubuntu 5.04
 :) 

1. Mine was a fersh install
2. Place your latest Cisco Client in your home directory.
3. Do a ```
sudo apt-get install build-essential
``` 
4. Do a ```
sudo apt-get install gcc
``` 
5. Do a uname -r  to find the correct kernel-headers for your build.
6. Use synaptic to search and install the correct kernel-HEADERS, not source.
7. Untar your Cisco Client, go to the vpnclient folder and do a ```
sudo sh vpn_install
``` 
8. Answer all questions, the defaults worked for me.
9. make sure you start the vpn sub-system with
```
sudo /etc/init.d/vpnclient_init start
``` 
10. Copy your .pcf profile to the ```
sudo cp <your .pcf> /etc/opt/cisco-vpnclient/Profiles
```.
11. Do a vpnclient connect <your profile> (without the .pcf extention)
12. Hope this helps.

Hemps 
:)[/QUOTE]


Thanks ...it worked for me..........thanks a zillion

Dan

---

### Post by jsares on 2005-08-03
I've got the client compiled and running but it seems to work for a while then die.  I don't think it's a driver issue because I have it installed on Fedora Core 4 on the same system and it doesn't have any problems.

When I connect I start to get huge packet loss (50-70%) doing pings to external servers then it just dies.

Any ideas?

Thanks,

Jason

---

### Post by jsares on 2005-08-04
Never mind the problem seems to have went away on it's own.

Jason

---

### Post by dmflad on 2005-08-21
Only lack of VPN-ability is stopping me from going all Ubuntu. Followed directs at [http://www.mcmaster.ca/cis/network/vpn/vpnclient_linux.htm](http://www.mcmaster.ca/cis/network/vpn/vpnclient_linux.htm) my (found by google-ing) but get error: 
   Cisco Systems VPN Client Version 4.6.00 (0045)
   Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.
   Client Type(s): Linux
   Running on: Linux 2.6.10-5-386 #1 Thu Aug 18 22:23:56 UTC 2005 i686
   Config file directory: /etc/opt/cisco-vpnclient

   Could not attach to driver. Is kernel module loaded?
   The application was unable to communicate with the VPN sub-system.

Checked bits posted on this forum but no luck. Didn't have this trouble w/RedHat install done while back. I've got my wireless, ICA, email, IM and Bluefish working. But need VPN and Oracle client running before MSWin leaves all my Dells.

So what's this noobish-one missing?

---

### Post by eschreib on 2005-10-08
Hi - i'm a serious noob and have fedora 2.6.13-1.1526_FC4
I think my cisco issue has something to do with the 'headers' anser above, but I have no idea what the above meant regarding:

[I]
[I]yes, it all depends on the kernel you are running.

Installed files indicates it puts everything in /usr/src/linux-headers-2.6.10-4-686 and that it left a symlink from /usr/src/linux to /usr/src/linux-headers-2.6.10-4-686.[/I][/I]

Here is my install error log:

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.

For RedHat 6.x users these files are installed in /usr/src/linux by default
For RedHat 7.x users these files are installed in /usr/src/linux-2.4 by default
For Suse 7.3 users these files are installed in /usr/src/linux-2.4.10.SuSE by default

Directory containing linux kernel source code [/lib/modules/2.6.13-1.1526_FC4/build]

* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.13-1.1526_FC4/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.13-1.1526_FC4/build" will be used to build the module.

Is the above correct [y]

Making module
In file included from linuxcniapi.c:19:
/usr/include/linux/modversions.h:1:2: error: #error Modules should never use kernel-headers system headers,
/usr/include/linux/modversions.h:2:2: error: #error but rather headers from the appropriate kernel package.
/usr/include/linux/modversions.h:3:2: error: #error Change -I/usr/src/linux/include (or similar) to
/usr/include/linux/modversions.h:4:2: error: #error -I/lib/modules/$(uname -r)/build/include
/usr/include/linux/modversions.h:5:2: error: #error to build against the currently-running kernel.

---

### Post by shadow07 on 2005-10-10
Well, I have the Cisco VPN Client installed, and the module loads just perfectly.  I am also able to load the kernel driver without issue.  I am also able to connect to a Cisco PIX firewall, and get an IP address.  However, I am UNABLE to get any traffic across the tunnel.

When I ping, I get "operation not permitted".  I also lose all local network connectivity.  Yes, the profile is setup to allow Local LAN Access.

Now, I am running Breezy right now, and I was able to connect over a week ago.  I am not sure if any of the packages/updates broke anything.

I'm going to post this in the Breezy Dev section, but just wanted to let everyone here know my situation.

---

### Post by VstarAl on 2005-10-18
[QUOTE=lildude]
2.  Ensure you are using gcc 3.x and not 4.0.  ([FONT=Courier New]*ls -l /usr/bin/gcc*[/FONT]).  If it points to gcc-4.0, change the symlink to point to gcc-3.x
[/QUOTE]

I'm very much a newbie to Linux.  I'm trying to install the Cisco VPN Client on Breezy (5.10) and am running into an error where it's looking for gcc-3.4.  I have it installed, but the gcc symlink is pointing to gcc-4.0.  How do I change the symlink so it points to gcc-3.4?

Thanks!

---

### Post by shadow07 on 2005-10-22
do the following

```
sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc /usr/bin/gcc-3.4
```

---

### Post by ChrisC on 2005-10-22
I understand that all this is about compiling the VPN client using the Cisco sources.  Does anyone know what the status is of making a Debian package available for this?  From an earlier comment I understand that it probably can't go into the Ubuntu archive due to Cisco's requirements, but is it available in another repository somewhere?  I sure would like to be able to keep my machine purely apt installed.  This scripted compilation stuff eventually leads to madness ...

---

### Post by ChrisC on 2005-10-23
Does anyone know what the status is of making a Debian package available for this?

---

### Post by spin2cool on 2005-10-24
I'm installing the Cisco vpn, and have followed all the directions faithfully.  When I try to run the vpn_install script, using the command "sudo sh vpn_install", I recieve the following error:

```
vpn_install: line 16: syntax error near unexpected token `elif'
'pn_install: line 16: `elif [ -x /bin/id ]; then

```

Any ideas what could be causing this?  Is this version of the installer script fubar?

for reference, here's the header of the script, including the part raising the error:
```

#! /bin/sh
##########################################################################
#           Copyright (c) 2001, Cisco Systems, All Rights Reserved
###########################################################################
#
#  File:    vpn_install
#  Date:    06/15/2001
#
###########################################################################
#
# linux VPN client installation script.
#
###########################################################################
if [ -x /usr/bin/id ]; then
    ID="/usr/bin/id"
elif [ -x /bin/id ]; then
    ID="/bin/id"
else
    echo "Unable to determine access level"
    exit 1
fi

```

---

### Post by ChrisC on 2005-10-24
Mmmmkay, moving along ...

I tried to install the vpnclient using the excellent 26-Apr procedure.  Alas, it ain't workin'.  I get "Invalid module format" when I try to start it.  *IN ADDITION* to the steps delineated in that procedure, I tried:
 - installing gcc-3.4
 - repointing the gcc symlink
 - patching interceptor.c per [http://rootsmith.ca/cisco-vpn.html](http://rootsmith.ca/cisco-vpn.html)
 - when that patch was partially rejected, I finished it manually
 - the skb_checksum_help lines (see above URL) aren't in the interceptor.c file that I've got

I think I saw another interceptor.c patch posted here somewhere, will go look for that ... tomorrow ...

Wishing for a Debian package ...

Note:  compilation and module newbie

---

### Post by spin2cool on 2005-10-24
As many others have done, I ended up using the vpnc client instead of the cisco one.  It works beautifully.  A search for 'vpnc' on these forums reveals several how-to threads on installing it and setting it up

---

### Post by VstarAl on 2005-10-24
[QUOTE=shadow07]do the following

```
sudo rm /usr/bin/gcc
sudo ln -s /usr/bin/gcc /usr/bin/gcc-3.4
```[/QUOTE]

Thanks!!  That worked.

---

### Post by evisboy on 2005-10-25
Here's my mini how-to for using VPNC: 

ok, unless you ABSOLUTELY are required to use the cisco client, I suggest you use VPNC.

sudo apt-get install vpnc

If you are using the cisco client b/c you need it to work w/ profiles, then open up the *.pcf file and open it in an editor. Here's an example:

[main]
Description=For Wireless Users on Campus
Host=10.10.222.215
AuthType=1
GroupName=mygroup
GroupPwd=
enc_GroupPwd=9C69679A8862C3A470444188779511217B111 F038F62083155F8924E1E94D54CC9334F883BDA022195A1D6C 8DEF18A29636165631C75AD77
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0


You will see a bunch of information. Follow the following format to create a conf file (sudo gedit /etc/vpnc/myfile.conf) that will be read by VPNC (change what's in bold):

IPSec gateway 10.10.222.215
IPSec ID mygroup
IPSec secret ClearTextPassword
Xauth username UserName

The tough part is the IPSec secret. If you're at a university, this will most likely be encrypted. Your conf file will need this in clear text. You can translate that by going here: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Just plug the cleartext secret into your new conf file, go back to terminal and type: sudo vpnc /etc/vpnc/myfile.conf and you will be connected!!

To disconnect, use: vpnc-disconnect

My suggestion is don't waste your time w/ the cisco client.

---

### Post by ChrisC on 2005-10-27
[QUOTE=spin2cool]I ended up using the vpnc client instead of the cisco one.  It works beautifully.[/QUOTE]

I had seen that option but something in the vpnc docs about it not working in a scenario (that sounded like mine) had spooked me from it.  But spin2cool's post prompted me to try it again.

It works!

Now, there's a big caveat.  The "group password", specified in the profile file on the "IPSec secret" line, needs to be IN THE CLEAR, NOT HASHED.  In my case, and I suspect many cases, that password is going to be hashed by your company (especially the big ones like mine) and they won't want to give you the unhashed password.  I begged for it, complaining that the Cisco client wouldn't work, and they gave it to me.

[upon preview] Oh my god, hash decode!  I didn't think that was realistically  possible, I thought these things were always one-way (obviously I wasn't a CS major).  Awesome.  Wooo, pure [syn]apt[ic] machine!  Now, on to Acrobat ... :)

---

### Post by ChrisC on 2005-10-27
Looking now for a little panel thingy to turn the VPN on and off:

[QUOTE=ACK!!]If your vpn does not do the yes/no authorization prompt after username and password challenge then you should try out the gnome vpn tools.  vpn-applet is the name of the package.  I cannot remember if I had to add a repo to get it or it is available in the regular ubuntu channels.[/QUOTE]

I don't find much googling for "vpn-applet" and there's nothing in the ubuntu repository for that package.  I heard about OpenVPN and it looks nice but OpenVPN seems to be mutually exclusive of vpnc, and I *just* got vpnc working, I think I'll stick with it :)

Is there a little Gnome GUI widget for vpnc control?  I haven't seen the new breezy Network Manager which supposedly has some VPN controls integrated into it.

---

### Post by shadow07 on 2005-10-29
[QUOTE=ChrisC]Looking now for a little panel thingy to turn the VPN on and off:



I don't find much googling for "vpn-applet" and there's nothing in the ubuntu repository for that package.  I heard about OpenVPN and it looks nice but OpenVPN seems to be mutually exclusive of vpnc, and I *just* got vpnc working, I think I'll stick with it :)

Is there a little Gnome GUI widget for vpnc control?  I haven't seen the new breezy Network Manager which supposedly has some VPN controls integrated into it.[/QUOTE]

I have the latest official Cisco VPN Client running on my Breezy machine.  I use GVPNDialer (which there is a package on Synaptic).

I do not know of one for VPNC.

If you want to try again with the Cisco client, email me and we can work on it offline.

---

### Post by jmwest1 on 2005-11-21
I've followed the How-To's without fail but continue to get the following:

[I]Starting /usr/local/bin/vpnclient: insmod: error inserting '/lib/modules/2.6.10-5-386/CiscoVPN/cisco_ipsec': -1 Invalid module format
Failed (insmod)
[/I]

I've succesfully installed and configured vpnc but receive the following when connecting to my PIX:

[I]vpnc: expected xauth packet; rejected: INVALID_EXCHANGE_TYPE
[/I]

I'm pretty sure we're using no-xauth in the PIX config.

All of this with 5.04 so I'm going to upgrade to 5.10 and try again. Has anyone had these problems and been able to overcome them?

---

### Post by windowsXuser on 2005-11-25
Hello agian,

I am currently trying to use a VPN to connect to my collece.
I have downloaded vpnc using apt-get install vpnc and managed to get the latest version.

I am just trying to figure out where it was downloaded and installed to.  I have checked  /bin, /sbin/, /usr/sbin/, /usr/local/bin and /opt.

I have looked in /etc/vpnc and all that's in there is a file named example.conf. 

I cant seem to find it. I need to locate it so i can edit the vpnc.conf file to configure to set the path of the host (which is my school)

Where are repositories usually installed. I am using Package Manager (Adept)

Thanks..

---

### Post by bin on 2005-11-25
I'm pretty sure that kvpnc is in the extended repositories - look for enable universe / multiverse. You'll be able to install through adept

It'll give you a nice gui for vpnc - BTW what sort of box are you trying to connect through - Cisco by any chance??

in light

bin

---

### Post by shakin on 2005-11-25
[QUOTE=windowsXuser]Hello agian,

I am currently trying to use a VPN to connect to my collece.
I have downloaded vpnc using apt-get install vpnc and managed to get the latest version.

I am just trying to figure out where it was downloaded and installed to.  I have checked  /bin, /sbin/, /usr/sbin/, /usr/local/bin and /opt.

I have looked in /etc/vpnc and all that's in there is a file named example.conf. 

I cant seem to find it. I need to locate it so i can edit the vpnc.conf file to configure to set the path of the host (which is my school)

Where are repositories usually installed. I am using Package Manager (Adept)

Thanks..[/QUOTE]

In Synaptic, right-click on the vpnc package and go to properties. After the proeprties dialog there will be an Installed Files tab. From there you can see where the executable has been installed.

However, a vpnc menu entry should have been installed so you shouldn't have to go searching for the executable.

---

### Post by dannemil on 2005-11-25
[QUOTE=evisboy]Here's my mini how-to for using VPNC: 

ok, unless you ABSOLUTELY are required to use the cisco client, I suggest you use VPNC.

sudo apt-get install vpnc

If you are using the cisco client b/c you need it to work w/ profiles, then open up the *.pcf file and open it in an editor. Here's an example:

[main]
Description=For Wireless Users on Campus
Host=10.10.222.215
AuthType=1
GroupName=mygroup
GroupPwd=
enc_GroupPwd=9C69679A8862C3A470444188779511217B111 F038F62083155F8924E1E94D54CC9334F883BDA022195A1D6C 8DEF18A29636165631C75AD77
EnableISPConnect=0
ISPConnectType=0
ISPConnect=
ISPCommand=
Username=
SaveUserPassword=0
UserPassword=
enc_UserPassword=
NTDomain=
EnableBackup=0
BackupServer=
EnableMSLogon=1
MSLogonType=0
EnableNat=1
TunnelingMode=0
TcpTunnelingPort=10000
CertStore=0
CertName=
CertPath=
CertSubjectName=
CertSerialHash=00000000000000000000000000000000
SendCertChain=0
PeerTimeout=90
EnableLocalLAN=0


You will see a bunch of information. Follow the following format to create a conf file (sudo gedit /etc/vpnc/myfile.conf) that will be read by VPNC (change what's in bold):

IPSec gateway 10.10.222.215
IPSec ID mygroup
IPSec secret ClearTextPassword
Xauth username UserName

The tough part is the IPSec secret. If you're at a university, this will most likely be encrypted. Your conf file will need this in clear text. You can translate that by going here: [http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode](http://www.unix-ag.uni-kl.de/~massar/bin/cisco-decode)

Just plug the cleartext secret into your new conf file, go back to terminal and type: sudo vpnc /etc/vpnc/myfile.conf and you will be connected!!

To disconnect, use: vpnc-disconnect

My suggestion is don't waste your time w/ the cisco client.[/QUOTE]


Thanks a bunch for this advice. Works like a charm. Makes it easier to upgrade the kernel without having to worry about losing the vpn client each time.

---

### Post by windowsXuser on 2005-11-25
[QUOTE=bin]I'm pretty sure that kvpnc is in the extended repositories - look for enable universe / multiverse. You'll be able to install through adept

It'll give you a nice gui for vpnc - BTW what sort of box are you trying to connect through - Cisco by any chance??

in light

bin[/QUOTE]

hey,

I am trying to connect through Cisco and would be great if you could give me a nice gui for vpnc.. I tried kvpnc, but keep getting errors with it, so i unistalled it.

Blair..

---

### Post by shadow07 on 2005-11-26
I was just able to install KVpnc on my Ubuntu Breezy install.  What errors were you getting?

---

### Post by windowsXuser on 2005-11-26
[QUOTE=shadow07]I was just able to install KVpnc on my Ubuntu Breezy install.  What errors were you getting?[/QUOTE]

Hey,

I dont think the error was because the program wasn't functioning properly, my settings are probably wrong to begin with.

It kept saying error - connection failed, then the application would close.

I am still trying to figure out how to use it.

Have fun.

Blair..

---

### Post by kiranbr on 2005-11-30
I am able to connect to my workplace using Cisco VPN, but the following strange problems are bugging me:

1) I can telnet to my office workstation, but large data transfers make the telnet session to hang. Ditto for ftp.

2) I try connecting to office using the Citrix ICA client, but whether I can connect or not seems to depend on the phase of the moon (i.e., it's very random). When I manage to connect, the connection is pretty stable (atleast as of now).

I played around with the MTU (setting it to 1492, 1408, 2000, you name it), but the random behaviour has not stopped. On any given trial, I *may* or *may not* connect.

I also tried to clamp the MSS (both to PMTU and to 1400), but even this hasn't solved the randomness issue.

BY THE WAY, WHAT IS THE interceptor.c PATCH WHICH IS BEING TALKED ABOUT HERE? IS THIS WHAT I'M MISSING?

PLEASE HELP ME!

Cheers
Kiran

---

### Post by shadow07 on 2005-12-01
The interceptor.c patch was to resolve the problem with compilation of the older Cisco VPN client ipsec module.  What version of the Cisco VPN Client for Linux are you running?

---

### Post by kiranbr on 2005-12-01
I'm using vpnclient-linux-4.6.00.0045-k9.tar.gz. I had no compilation issues.

Cheers
Kiran

---

### Post by h0meb0y25 on 2006-08-13
I m trying to run following but getting error.. Help will be hgihly appreciated.

thnx much,
-s

root@ubuntu:~# sudo apt-get install vpnc
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package vpnc
root@ubuntu:~#

---

### Post by joris1977 on 2006-08-15
To get acces to the digital library from my university (universiteit van Amsterdam) on my home computer, i have to use a vpn-tunnel. For windows the university gives a nice cisco installer that works fine and they give support if it fails. But i don't want to switch all the time between ubuntu and windows. So I like to get it running with ubuntu. They give you acces to a 
cisco linux installer, but they allready mention to try it on your own risk  and they will not give any support...

I a serious noob and following the instructions in this forum gives me the following: 

joris@Ruuf:~/vpnclient$ sudo sh vpn_install
Cisco Systems VPN Client Version 4.6.02 (0030) Linux Installer
Copyright (C) 1998-2004 Cisco Systems, Inc. All Rights Reserved.

By installing this product you agree that you have read the
license.txt file (The VPN Client license) and will comply with
its terms.


Directory where binaries will be installed [/usr/local/bin]

Automatically start the VPN service at boot time [yes]

In order to build the VPN kernel module, you must have the
kernel headers for the version of the kernel you are running.


Directory containing linux kernel source code [/lib/modules/2.6.15-26-686/build]
* Binaries will be installed in "/usr/local/bin".
* Modules will be installed in "/lib/modules/2.6.15-26-686/CiscoVPN".
* The VPN service will be started AUTOMATICALLY at boot time.
* Kernel source from "/lib/modules/2.6.15-26-686/build" will be used to build the module.

Is the above correct [y]

Making module
make -C /lib/modules/2.6.15-26-686/build SUBDIRS=/home/joris/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.15-26-686'
  CC [M]  /home/joris/vpnclient/linuxcniapi.o
/home/joris/vpnclient/linuxcniapi.c: In function ‘CniInjectReceive’:
/home/joris/vpnclient/linuxcniapi.c:312: error: ‘struct sk_buff’ has no member named ‘stamp’
/home/joris/vpnclient/linuxcniapi.c: In function ‘CniInjectSend’:
/home/joris/vpnclient/linuxcniapi.c:452: error: ‘struct sk_buff’ has no member named ‘stamp’
make[2]: *** [/home/joris/vpnclient/linuxcniapi.o] Error 1
make[1]: *** [_module_/home/joris/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.15-26-686'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Maybe someone has any idea to solve this... I also tried the vpnc mentioned 
in this thread, but this howto is to difficult for me. I found the UvaVPN.pcf file. But where do I find this ipsec secret so i can translate it to text. If it helps i can post the pcf file, so someone can point me to 
it...

I also checked a lot of other posts on this forum and with google but couldn't find any solution...

Hope someone can help me out.

greetings

Joris

:)  edit: I found the solution: For some reason Cisco VPN-Client version 4.6.02  doesn't work with the dapper-version i'm using. When i tried with version 4.8 it installed without errors and vpn is working nice. Don't know why the university still spreads the old version, for other mac and windows they use a 4.8 version.

---

### Post by mithras86 on 2006-08-28
Just like many others, i've got the same problem with installing the vpn client. The terminal output doesn't give much information:
```
Making module
make -C /lib/modules/2.6.15-26-386/build SUBDIRS=/home/jurian/Software/Internet/Cisco VPN client modules
make[1]: Map '/usr/src/linux-headers-2.6.15-26-386' wordt binnengegaan
make[1]: *** Er is geen regel om doel 'VPN' te maken.  Gestopt.
make[1]: Map '/usr/src/linux-headers-2.6.15-26-386' wordt verlaten
make: *** [default] Fout 2
Failed to make module "cisco_ipsec.ko".
jurian@jvs:~/Software/Internet/Cisco VPN client$ 
```I know this is dutch, but the 3rd rule means the folder is entered, the 4th rule that there isn't a rule to make the target 'VPN'. Then it stops. 
Does anyone how to fix this problem? I've got gcc pointing to gcc3.4 and installed the kernel headers correctly.

---

### Post by SangLad on 2007-04-14
I am a novice and having the following problems... Hope someone can help me out...

root@slee-laptop:/home/slee# vpnclient connect Partners
Cisco Systems VPN Client Version 4.7.00 (0640)
Copyright (C) 1998-2005 Cisco Systems, Inc. All Rights Reserved.
Client Type(s): Linux
Running on: Linux 2.6.20-15-generic #2 SMP Fri Apr 13 16:33:26 UTC 2007 i686
Config file directory: /etc/opt/cisco-vpnclient

Initializing the VPN connection.
Secure VPN Connection terminated locally by the Client
Reason: Bad Parameter.
There are no new notification messages at this time.

---

### Post by joefx23 on 2007-04-20
check the profile "Partners" you are loading .. i think there is a problem

---

### Post by hackmeister on 2008-06-08
If anyone is looking for a package for Gvpndialer I've created one for Hardy:
[http://pdavila.homelinux.org:8080/blog/?p=291](http://pdavila.homelinux.org:8080/blog/?p=291)

---

