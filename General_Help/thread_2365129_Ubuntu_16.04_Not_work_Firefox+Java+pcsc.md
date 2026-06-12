---
title: "Ubuntu 16.04 Not work Firefox+Java+pcsc"
date: 2017-07-03
forum: General Help
---

### Post by nifanin1990 on 2017-07-03
Good afternoon!

I'm trying to set up an electronic card reader with one site on Ubuntu 16.04. The site gave instructions that you need to install Firefox + Java. The pcscd daemon and, correspondingly, the driver are responsible for the operation of the reader itself. ACS ACR1281U-C1 reader.

The driver is taken from the pcsc-lite-acsccid package.
The pcsc_scan program correctly finds the reader and responds to the insert / pull out of the card.
Java I put on the manual [http://help.ubuntu.ru/wiki/java](http://help.ubuntu.ru/wiki/java). I tried different installation methods, different versions, different vendors, different software (JDK and JRE). I reinstalled Ubuntu several times.
Firefox tried to install from the repository, from the source, portables ...

But in the end everything is useless: Firefox normally sees Java in plug-ins, pcscd is a scanner, but the site stubbornly writes "Reader not detected."

All anything, but I downloaded ALTLinux and tried to install it on it - it all worked out in a couple of hours of setup.

Tried similar actions on Ubuntu - does not leave anything.

In the end, it turns out that you do not want to leave Ubuntu, but it's specifically for this implementation that it does not show itself with the best of luck.

Actually, I ask you to help me understand this issue.

First I'll tell you about AltLinux, and after about Ubuntu

I download from the office. Site AltLinux 7

```

[root@host-93 ~]# cat /etc/altlinux-release 
ALT Linux 7.0.5 Centaurus  (Pholus)
[root@host-93 ~]# uname -a
Linux host-93.localdomain 3.14.41-std-def-alt1 #1 SMP Thu May 7 12:49:34 UTC 2015 i686 GNU/Linux

```

Next, I installed:
Firefox 38.4.0 ESR from [https://ftp.mozilla.org/pub/firefox/releases/38.4.0esr/linux-i686/en/firefox-38.4.0esr.tar.bz2](https://ftp.mozilla.org/pub/firefox/releases/38.4.0esr/linux-i686/en/firefox-38.4.0esr.tar.bz2)
Java JRE from [http://ftp.osuosl.org/pub/funtoo/distfiles/oracle-java/jre-7u80-linux-i586.tar.gz](http://ftp.osuosl.org/pub/funtoo/distfiles/oracle-java/jre-7u80-linux-i586.tar.gz)
Drivers from the pcsc-lite-acsccid and pcsc-lite-asedriveiiie-usb packages

As a result, the set of installation commands from a clean installation was as follows:


```

mkdir /usr/java
wget http://ftp.osuosl.org/pub/funtoo/distfiles/oracle-java/jre-7u80-linux-i586.tar.gz
mv jre-7u60-linux-i586.tar.gz /usr/java/
cd /usr/java/
tar zxvf jre-7u60-linux-i586.tar.gz 
rm jre-7u60-linux-i586.tar.gz 
mkdir /usr/lib/mozilla/plugins
cd /usr/lib/mozilla/plugins
ln -s /usr/java/jre1.7.0_60/lib/i386/libnpjp2.so 

apt-get update
apt-get install pcsc-lite-asedriveiiie-usb pcsc-lite  libpcsclite pcsc-tools opensc libhal pcsc-lite-acsccid
service pcscd restart

wget https://ftp.mozilla.org/pub/firefox/releases/38.4.0esr/linux-i686/ru/firefox-38.4.0esr.tar.bz2
tar xf firefox-38.4.0esr.tar.bz2 
mv firefox /usr/local/
mv /usr/bin/firefox /usr/bin/firefox-old
ln -s /usr/local/firefox/firefox /usr/bin/firefox


rm /etc/alternatives/links/\|usr\|bin\|java
ln -s '/etc/alternatives/links/|usr|bin|java' /usr/java/jre1.7.0_80/bin/java
ln -s /usr/java/jre1.7.0_80/bin/java '/etc/alternatives/links/|usr|bin|java' 
ln -s /usr/java/jre1.7.0_80/bin/jcontrol '/etc/alternatives/links/|usr|bin|jcontrol' 
rm '/etc/alternatives/links/|usr|bin|jcontrol'
ln -s /usr/java/jre1.7.0_80/bin/jcontrol '/etc/alternatives/links/|usr|bin|jcontrol' 
rm '/etc/alternatives/links/|usr|bin|keytool'
ln -s /usr/java/jre1.7.0_80/bin/keytool '/etc/alternatives/links/|usr|bin|keytool' 
rm '/etc/alternatives/links/|usr|bin||usr|lib|browser-plugins|libjavaplugin_oji.so'
rm '/etc/alternatives/links/|usr|lib|browser-plugins|libjavaplugin_oji.so'
ln -s /usr/java/jre1.7.0_80/lib/i386/libnpjp2.so '/etc/alternatives/links/|usr|lib|browser-plugins|libjavaplugin_oji.so'


```


After that, I ran jcontrol from the user, registered the site address in the Security tab and chose Security Level - Medium.

After connecting to the site everything works!


[http://imgur.com/GMAU0oo](http://imgur.com/GMAU0oo)
[http://imgur.com/if0tBYS](http://imgur.com/if0tBYS)

Extras. information:

```


[root@host-93 ~]# systemctl status pcscd
pcscd.service - PC/SC Smart Card Daemon
   Loaded: loaded (/lib/systemd/system/pcscd.service; static)
   Active: inactive (dead) since &#1055;&#1090; 2017-06-23 17:37:21 MSK; 2min 35s ago
  Process: 4715 ExecStart=/usr/sbin/pcscd --foreground --auto-exit (code=exited, status=0/SUCCESS)

&#1080;&#1102;&#1085; 23 17:33:24 host-93.localdomain systemd[1]: Starting PC/SC Smart Card Daemon...
&#1080;&#1102;&#1085; 23 17:33:24 host-93.localdomain systemd[1]: Started PC/SC Smart Card Daemon.
&#1080;&#1102;&#1085; 23 17:33:24 host-93.localdomain pcscd[4715]: Error: can't open /var/run/openct/status: No such file or directory
&#1080;&#1102;&#1085; 23 17:33:24 host-93.localdomain pcscd[4715]: 00000000 readerfactory.c:1110:RFInitializeReader() Open Port 0x200000 Fail...2/005)
&#1080;&#1102;&#1085; 23 17:33:24 host-93.localdomain pcscd[4715]: 00000013 readerfactory.c:375:RFAddReader() Generic CCID Reader init failed.
&#1080;&#1102;&#1085; 23 17:33:24 host-93.localdomain pcscd[4715]: 00000028 hotplug_libudev.c:520:HPAddDevice() Failed adding USB device: Gen...Reader
&#1080;&#1102;&#1085; 23 17:33:39 host-93.localdomain pcscd[4715]: 15320438 ccid_usb.c:638:WriteUSB() write failed (2/5): -4 No such device
&#1080;&#1102;&#1085; 23 17:33:51 host-93.localdomain pcscd[4715]: 12005469 commands.c:231:CmdPowerOn Card absent or mute
&#1080;&#1102;&#1085; 23 17:33:51 host-93.localdomain pcscd[4715]: 00000487 ifdhandler.c:1434:IFDHPowerICC() PowerUp failed
&#1080;&#1102;&#1085; 23 17:33:51 host-93.localdomain pcscd[4715]: 00000290 eventhandler.c:302:EHStatusHandlerThread() Error powering up card...100016
[root@host-93 ~]# pcsc_scan 
PC/SC device scanner
V 1.4.27 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.8.8
Using reader plug'n play mechanism
Scanning present readers...
0: ACS ACR1281 1S Dual Reader 00 00
1: ACS ACR1281 1S Dual Reader 00 01
2: ACS ACR1281 1S Dual Reader 00 02

Fri Jun 23 17:40:22 2017
Reader 0: ACS ACR1281 1S Dual Reader 00 00
  Card state: Card removed, 
Reader 1: ACS ACR1281 1S Dual Reader 00 01
  Card state: Card removed, 
Reader 2: ACS ACR1281 1S Dual Reader 00 02
  Card state: Card removed, 
^C
[root@host-93 ~]# ls -la /usr/bin/java 
lrwxrwxrwx 1 root root 37 &#1080;&#1102;&#1085; 22 17:08 /usr/bin/java -> /etc/alternatives/links/|usr|bin|java
[root@host-93 ~]# ls -la '/etc/alternatives/links/|usr|bin|java'
lrwxrwxrwx 1 root root 30 &#1080;&#1102;&#1085; 23 13:36 /etc/alternatives/links/|usr|bin|java -> /usr/java/jre1.7.0_80/bin/java
[root@host-93 ~]# 


```

But when you try to do something like this on Ubuntu, nothing happens.


[http://imgur.com/zZhVnJZ](http://imgur.com/zZhVnJZ)
[http://imgur.com/ZQweywa](http://imgur.com/ZQweywa)


```

root@tk16:~# cat /etc/debian_version 
stretch/sid
root@tk16:~# uname -a
Linux tk16 4.8.0-36-generic #36~16.04.1-Ubuntu SMP Sun Feb 5 09:39:41 UTC 2017 i686 i686 i686 GNU/Linux


```

Versions and methods for installing Java, Firefox, pcsc, drivers are completely similar.

```

mkdir /usr/java
wget http://ftp.osuosl.org/pub/funtoo/distfiles/oracle-java/jre-7u80-linux-i586.tar.gz
mv jre-7u80-linux-i586.tar.gz /usr/java/
cd /usr/java/
tar xf jre-7u80-linux-i586.tar.gz
rm jre-7u80-linux-i586.tar.gz
mkdir -p /usr/lib/mozilla/plugins
cd /usr/lib/mozilla/plugins
ln -s /usr/java/jre1.7.0_80/lib/i386/libnpjp2.so
rm libjavaplugin.so
ln -s /usr/java/jre1.7.0_80/lib/i386/libnpjp2.so libjavaplugin.so




apt-get install libpcsclite-dev libpcsclite1 libacsccid1 libasedrive-serial libasedrive-usb libccid libhbalinux-dev opensc pcsc-tools
service pcscd restart
systemctl enable pcscd

cd ~
wget https://ftp.mozilla.org/pub/firefox/releases/38.4.0esr/linux-i686/ru/firefox-38.4.0esr.tar.bz2
tar xf firefox-38.4.0esr.tar.bz2 
mv firefox /usr/local/
mv /usr/bin/firefox /usr/bin/firefox-old
ln -s /usr/local/firefox/firefox /usr/bin/firefox

ln -sf /usr/java/jre1.7.0_80/bin/* /usr/bin

```


Of course to run jcontrol and register in the Security address of the site and Security Level - Medium, I did not forget.

```

root@tk16:~# systemctl status pcscd
&#9679; pcscd.service - PC/SC Smart Card Daemon
   Loaded: loaded (/lib/systemd/system/pcscd.service; indirect; vendor preset: enabled)
   Active: inactive (dead) since &#1055;&#1090; 2017-06-23 17:54:45 MSK; 6s ago
  Process: 2486 ExecStart=/usr/sbin/pcscd --foreground --auto-exit (code=exited, status=0/SUCCESS)
 Main PID: 2486 (code=exited, status=0/SUCCESS)

&#1080;&#1102;&#1085; 23 17:53:42 tk16 systemd[1]: Started PC/SC Smart Card Daemon.
&#1080;&#1102;&#1085; 23 17:53:42 tk16 pcscd[2486]: 00000000 readerfactory.c:1043:RFInitializeReader() Open Port 0x0 Failed (/dev/ttyS3)
&#1080;&#1102;&#1085; 23 17:53:42 tk16 pcscd[2486]: 00000013 readerfactory.c:335:RFAddReader() ASEDriveIIIe Serial Reader init failed.
&#1080;&#1102;&#1085; 23 17:53:42 tk16 pcscd[2486]: 00422509 commands.c:250:CmdPowerOn Card absent or mute
&#1080;&#1102;&#1085; 23 17:53:42 tk16 pcscd[2486]: 00018834 commands.c:250:CmdPowerOn Card absent or mute
&#1080;&#1102;&#1085; 23 17:53:42 tk16 pcscd[2486]: 00000326 ifdhandler.c:1415:IFDHPowerICC() PowerUp failed
&#1080;&#1102;&#1085; 23 17:53:42 tk16 pcscd[2486]: 00000193 eventhandler.c:304:EHStatusHandlerThread() Error powering up card: -2146435050 0x80100016
root@tk16:~# pcsc_scan 
PC/SC device scanner
V 1.4.25 (c) 2001-2011, Ludovic Rousseau <ludovic.rousseau@free.fr>
Compiled with PC/SC lite version: 1.8.14
Using reader plug'n play mechanism
Scanning present readers...
0: ACS ACR1281 1S Dual Reader 00 00
1: ACS ACR1281 1S Dual Reader 00 01
2: ACS ACR1281 1S Dual Reader 00 02

Fri Jun 23 17:53:43 2017
Reader 0: ACS ACR1281 1S Dual Reader 00 00
  Card state: Card removed, 
Reader 1: ACS ACR1281 1S Dual Reader 00 01
  Card state: Card removed, 
Reader 2: ACS ACR1281 1S Dual Reader 00 02
  Card state: Card inserted, Unresponsive card, 
^C
root@tk16:~# ls -al /usr/bin/java
lrwxrwxrwx 1 root root 30 &#1080;&#1102;&#1085; 23 16:57 /usr/bin/java -> /usr/java/jre1.7.0_80/bin/java


```

In general, it is completely analogous with AltLinux installation, but none of this is obtained.

It would be nice to install other Java, Firefox, etc., but this does not help. I check it all 2 weeks and nothing changes.

On Windows, by the way, it also starts normally. But well, it's far away from this Windows.

Tell me, do you have any idea what might be the problem specifically in Ubuntu?

P.S. Apt-get update && apt-get upgrade does not change the situation. Checked.

---

### Post by nifanin1990 on 2017-07-04
The pump method helped:

As it turned out, the whole thing in the libpcsclite.so library
In AltLinux, it lies in the /usr/lib directory and java expects to find it there. And finds.
And  in Ubuntu it lies in /usr/lib/i386-linux-gnu/ and in the end java  can not find it and therefore the electronic card reader does not work.

The  most unpleasant thing is that there was not even an error about the  missing file in the directory, and therefore it was necessary to get to  the solution of this problem by typing.

Decision:
```

cd /usr/lib/
ln -s /usr/lib/i386-linux-gnu/libpcsclite.so
```

After that, everything worked as it should.

---

