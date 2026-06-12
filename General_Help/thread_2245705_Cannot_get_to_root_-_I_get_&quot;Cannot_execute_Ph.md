---
title: "Cannot get to root - I get &quot;Cannot execute Philross: No such file or directory"
date: 2014-09-25
forum: General Help
---

### Post by rossdotcom on 2014-09-25
Hi there,
I was trying to change my shell from bash to dash, using chsh ! ... when I received "Enter the new value, or press ENTER for the default
    Login Shell [/bin/dash]: ", I put my name ie philross ! ... Now when I try chsh I get "chsh: PAM: Authentication failure", so I then attempt to go into root to effect a repair ! I then use 'su -' to go into root, i get the password prompt up no problem, I then put in my password to which I then receive the following message - "Cannot execute Philross: No such file or directory", I have tried for hours to fix this but so far nothing .... I would really appreciate some help on this.
I would still like change from bash to dash - especially as I hear of the new 'shellshock' bug which does not affect ubuntu systems that primarily use dash or so I understand ...
I am running ubuntu 14.04 on a Dell inspiron 1525 laptop with up to now no problems ! ...
Kind regards
Phil Ross

---

### Post by Impavidus on 2014-09-25
It seems that you changed your shell to your user name, which is of course not a shell. Did you change it for your user or for root? To see what is going on exactly, have a look at the /etc/passwd file. It lists for each user the shell he wants to use. Don't worry, you can post the contents if you like, or just censor the unnecessary details. /etc/passwd no longer contains the hashes of the passwords.

As to that bug, security in Ubuntu comes in several layers, and this affects only one layer. Attackers would still need a way to get access to a shell. And a patch has already been distributed.

---

### Post by rossdotcom on 2014-09-26
Hi and thanks so much for your reply - I guess I changed it for root, I  have had a look at /etc/passwd with gedit, and these are the contents:
```

root::0:0:root:/root:Philross
daemon::1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin::2:2:bin:/bin:/usr/sbin/nologin
sys::3:3:sys:/dev:/usr/sbin/nologin
sync::4:65534:sync:/bin:/bin/sync
games::5:60:games:/usr/games:/usr/sbin/nologin
man::6:12:man:/var/cache/man:/usr/sbin/nologin
lp::7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail::8:8:mail:/var/mail:/usr/sbin/nologin
news::9:9:news:/var/spool/news:/usr/sbin/nologin
uucp::10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy::13:13:proxy:/bin:/usr/sbin/nologin
www-data::33:33:www-data:/var/www:/usr/sbin/nologin
backup::34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats::41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody::65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid::100:101::/var/lib/libuuid:
syslog::101:104::/home/syslog:/bin/false
messagebus::102:106::/var/run/dbus:/bin/false
usbmux::103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq::104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
kernoops::106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit::107:114:RealtimeKit,,,:/proc:/bin/false
saned::108:115::/home/saned:/bin/false
whoopsie::109:116::/nonexistent:/bin/false
speech-dispatcher:x:110:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
avahi::111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm::112:118:Light Display Manager:/var/lib/lightdm:/bin/false
colord::113:121:colord colour management daemon,,,:/var/lib/colord:/bin/false
hplip::114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
pulse::115:122:PulseAudio daemon,,,:/var/run/pulse:/bin/false
philrossdell::1000:1000:philross,,,:/home/philrossdell:/bin/dash
statd::116:65534::/var/lib/nfs:/bin/false
smbguest::1001:1001:Samba guest account:/dev/null:/dev/null
gdm::117:125:Gnome Display Manager:/var/lib/gdm:/bin/false
debian-spamd::118:126::/var/lib/spamassassin:/bin/sh
geoclue::119:127::/var/lib/geoclue:/bin/false

```
I have tried to make a correction but it wont let me save my changes ...
Look forward to hearing from you
Phil Ross

---

### Post by steeldriver on 2014-09-26
It's hard to see a way out of that that doesn't involve booting from a live CD / USB so that you can edit /etc/passwd with privileges - even recovery mode is not going to work without a valid login shell for root, I think

---

### Post by rossdotcom on 2014-09-26
Hi and thanks so much for your reply - I guess I changed it for root, I  have had a look at /etc/passwd with gedit, and these are the contents:
root::0:0:root:/root:Philross
daemon::1:1:daemon:/usr/sbin:/usr/sbin/nologin
bin::2:2:bin:/bin:/usr/sbin/nologin
sys::3:3:sys:/dev:/usr/sbin/nologin
sync::4:65534:sync:/bin:/bin/sync
games::5:60:games:/usr/games:/usr/sbin/nologin
man::6:12:man:/var/cache/man:/usr/sbin/nologin
lp::7:7:lp:/var/spool/lpd:/usr/sbin/nologin
mail::8:8:mail:/var/mail:/usr/sbin/nologin
news::9:9:news:/var/spool/news:/usr/sbin/nologin
uucp::10:10:uucp:/var/spool/uucp:/usr/sbin/nologin
proxy::13:13:proxy:/bin:/usr/sbin/nologin
www-data::33:33:www-data:/var/www:/usr/sbin/nologin
backup::34:34:backup:/var/backups:/usr/sbin/nologin
list:x:38:38:Mailing List Manager:/var/list:/usr/sbin/nologin
irc:x:39:39:ircd:/var/run/ircd:/usr/sbin/nologin
gnats::41:41:Gnats Bug-Reporting System (admin):/var/lib/gnats:/usr/sbin/nologin
nobody::65534:65534:nobody:/nonexistent:/usr/sbin/nologin
libuuid::100:101::/var/lib/libuuid:
syslog::101:104::/home/syslog:/bin/false
messagebus::102:106::/var/run/dbus:/bin/false
usbmux::103:46:usbmux daemon,,,:/home/usbmux:/bin/false
dnsmasq::104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
kernoops::106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
rtkit::107:114:RealtimeKit,,,:/proc:/bin/false
saned::108:115::/home/saned:/bin/false
whoopsie::109:116::/nonexistent:/bin/false
speech-dispatcher:x:110:29:Speech Dispatcher,,,:/var/run/speech-dispatcher:/bin/sh
avahi::111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
lightdm::112:118:Light Display Manager:/var/lib/lightdm:/bin/false
colord::113:121:colord colour management daemon,,,:/var/lib/colord:/bin/false
hplip::114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
pulse::115:122:PulseAudio daemon,,,:/var/run/pulse:/bin/false
philrossdell::1000:1000:philross,,,:/home/philrossdell:/bin/dash
statd::116:65534::/var/lib/nfs:/bin/false
smbguest::1001:1001:Samba guest account:/dev/null:/dev/null
gdm::117:125:Gnome Display Manager:/var/lib/gdm:/bin/false
debian-spamd::118:126::/var/lib/spamassassin:/bin/sh
geoclue::119:127::/var/lib/geoclue:/bin/false
I have tried to make a correction but it wont let me save my changes ...
Look forward to hearing from you
Phil Ross

---

### Post by rossdotcom on 2014-09-26
Hi and thanks for your reply.
When you say 'live cd'  would that be the cd that I made out of an iso image file and was used to install ubuntu onto my computer?
Phil

---

### Post by steeldriver on 2014-09-26
Yes that would do if you have it to hand (although you could use a smaller / lighter dedicated iso such as [http://www.sysresccd.org/](http://www.sysresccd.org/)). Make sure to select the **Try Ubuntu** option **not** the install option

You will then need to identify your installed system partition and mount it somewhere in the live filesystem so that you can edit the file. Alternatively you could try to use a chroot environment but that's more complicated and tbh I'm not sure that would even work without a valid shell for root on the target system.

---

### Post by rossdotcom on 2014-09-26
Hi and thanks,
Do you know what changes I need to make when I get the live CD etc up and running ?
Regards
Phil

---

### Post by spjackson on 2014-09-26
A live CD is one way to fix this. However, a broken root shell does not stop sudo working properly and you can therefore fix it with vipw (if you know how to use vi).
```

$ sudo chsh root
Changing the login shell for root
Enter the new value, or press ENTER for the default
        Login Shell [/bin/bash]: Philross
chsh: Warning: Philross does not exist
$ head -1 /etc/passwd
root:x:0:0:root:/root:Philross
$ sudo chsh root
Password: 
chsh: PAM: Authentication failure
$ sudo vipw 
You have modified /etc/passwd.
You may need to modify /etc/shadow for consistency.
Please use the command 'vipw -s' to do so.
$ head -1 /etc/passwd
root:x:0:0:root:/root:/bin/bash
$ 

```

---

### Post by rossdotcom on 2014-09-26
Hi, 
I have tried typing sudo chsh root and this is the response I get ...
 "$ sudo chsh root
[sudo] password for philrossdell: 
Password: 
chsh: PAM: Authentication failure
then if I follow your code I get exactly what you have put however at $ sudo vipw I get the complete contents of 'passwd' ... which tells me its a read only file ... sorry I am really new to all of this ...
Phil

---

### Post by Impavidus on 2014-09-26
You can no longer open a root shell, but sudo may still work. If it doesn't work, you have to boot from a live disk, mount the partition of your installed Ubuntu and do it from there. In principle any text editor with root permissions could do the trick. **vipw** is basically the vim text editor with some extra checks in place to prevent corruption of these important files. To use vipw from your installed system, use```
sudo vipw
``` or, from the live disk, mount the partition and use```
sudo vipw -R /path/to/mountpoint
```(Substitute the mount point of your root partition)
If you don't know how to use vim, use a different text editor. I recommend you first make a backup of this broken passwd file, in case something goes wrong and you get into an even greater mess. Then modify the first line (root's entry) by changing the part after the  last colon, which now reads **Philross**, to the desired shell, like  **/bin/dash**.

---

