---
title: ":/bin/false and :/nonexistent in /etc/passwd entries"
date: 2014-10-13
forum: General Help
---

### Post by Cbhihe on 2014-10-13
I reviewed my [FONT=courier new]/etc/passwd[/FONT] entries and would like to understand some of its entries, namely those showing [FONT=courier new]:/nonexistent[/FONT] and [FONT=courier new]:/bin/false[/FONT]. What do those two mean ? In particular looking into[FONT=courier new] /bin/false[/FONT], I got:
```
>  more /bin/false
******** /bin/false: Not a text file ********
```
Thanks. -ced

```
> more /etc/passwd | egrep -i "/bin/false" | sort 
avahi-autoipd:x:105:113:Avahi autoip daemon,,,:/var/lib/avahi-autoipd:/bin/false
avahi:x:111:117:Avahi mDNS daemon,,,:/var/run/avahi-daemon:/bin/false
colord:x:113:121:colord colour management daemon,,,:/var/lib/colord:/bin/false
dnsmasq:x:104:65534:dnsmasq,,,:/var/lib/misc:/bin/false
ftp:x:118:128:ftp daemon,,,:/srv/ftp:/bin/false
hplip:x:114:7:HPLIP system user,,,:/var/run/hplip:/bin/false
kernoops:x:106:65534:Kernel Oops Tracking Daemon,,,:/:/bin/false
lightdm:x:112:118:Light Display Manager:/var/lib/lightdm:/bin/false
messagebus:x:102:106::/var/run/dbus:/bin/false
mysql:x:119:129:MySQL Server,,,:/nonexistent:/bin/false
postfix:x:117:126::/var/spool/postfix:/bin/false
pulse:x:115:122:PulseAudio daemon,,,:/var/run/pulse:/bin/false
rtkit:x:107:114:RealtimeKit,,,:/proc:/bin/false
saned:x:108:115::/home/saned:/bin/false
syslog:x:101:104::/home/syslog:/bin/false
usbmux:x:103:46:usbmux daemon,,,:/home/usbmux:/bin/false
whoopsie:x:109:116::/nonexistent:/bin/false
``````

```

---

### Post by Lars Noodén on 2014-10-13
/bin/false is a program that always returns a status code indicating failure (a status code of 1).   It is used in the /etc/passwd file for an account's default shell to help prevent using said accounts for login access.  

Same for an account's home directory.  By setting it to a non-existent folder, it has n where to go and nowhere for programs or scripts that use the $HOME variable to write.  

For the format of the /etc/passwd account register see the manual page for the file format [passwd](http://manpages.ubuntu.com/manpages/trusty/en/man5/passwd.5.html).  It is a colon-separated list.  One record (account) per line, with each field separated by a colon:

```

man 5 passwd
```

Note the 5 there.  Leaving it out will make man default to the manual page for the *program* [passwd](http://manpages.ubuntu.com/manpages/trusty/en/man1/passwd.1.html) instead of the *file format* [passwd](http://manpages.ubuntu.com/manpages/trusty/en/man5/passwd.5.html)

---

### Post by Cbhihe on 2014-10-13
Thanks very much, Lars. Perfect answer. 
(I had looked up [FONT=courier new]man passwd[/FONT] and not [FONT=courier new]man 5 passwd[/FONT].)

---

### Post by Lars Noodén on 2014-10-13
No worries.  

Section 5 is for file formats and other conventions.  You kind of have to remember it is there, same for section 7.  Because if there is another man page with the same name but in an earlier section, the earlier section will be shown if no number is specified.  

Mostly these are hinted at in the 'see also' section at the bottom of the man page.  In the case of passwd(1), you'll see a mention of passwd(5) among others.  If I can't find what I wanted in the main part of the page, I alway scroll down to the 'see also' section because related pages usually get listed there.

---

