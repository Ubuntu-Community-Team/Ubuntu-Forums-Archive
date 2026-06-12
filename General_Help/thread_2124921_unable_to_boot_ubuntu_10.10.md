---
title: "unable to boot ubuntu 10.10"
date: 2013-03-12
forum: General Help
---

### Post by rezanabavi on 2013-03-12
Dear All,
I'm using ubuntu 10.10. I cant not boot to Genom and got the following errors in start up, could you please help me?:(

[COLOR=#000000][FONT=Droid Arabic Naskh]AppArmor parser error for etc/apparmor.d/gdm-guest-session in /etc/apparrmor.d/gdm-guest-session at line 5: could not open 'tunables/global'[/FONT][/COLOR]
[COLOR=#000000][FONT=Droid Arabic Naskh]AppArmor parser error for etc/apparmor.d/sbin.dhclient3 in /etc/apparrmor.d/sbin.dhclient3 at line 4: could not open 'tunables/global'[/FONT][/COLOR]
[COLOR=#000000][FONT=Droid Arabic Naskh]AppArmor parser error for etc/apparmor.d/usr.bin.evince in /etc/apparrmor.d/usr.bin.evince at line 6: could not open 'tunables/global'[/FONT][/COLOR]
[COLOR=#000000][FONT=Droid Arabic Naskh]AppArmor parser error for etc/apparmor.d/usr.bin.cupsd in /etc/apparrmor.d/usr.bin.cupsd at line 5: could not open 'tunables/global'[/FONT][/COLOR]
[COLOR=#000000][FONT=Droid Arabic Naskh]AppArmor parser error for etc/apparmor.d/usr.bin.tcpdump in /etc/apparrmor.d/usr.bin.tcpdump at line 4: could not open 'tunables/global'[/FONT][/COLOR]

---

### Post by sanderj on 2013-03-12
Ubuntu 10.10? You now that that version is not supported anymore? See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

I checked my own Ubuntu:

```
sander@flappie:~$ locate tunables | grep global
/etc/apparmor.d/tunables/global

sander@flappie:~$ dpkg -S  /etc/apparmor.d/tunables/global
apparmor: /etc/apparmor.d/tunables/global
```

... so: remove and then re-install "apparmor" and see if the error goes away.

---

### Post by dino99 on 2013-03-12
as i does not know what genom is (and you dont tell us), what i'm seeing is that "tunables/global", which might be only known by yourself
eventually you can try to boot without that option, by commenting out the line:

sudo gedit /etc/apparmor.d/....

---

### Post by rezanabavi on 2013-03-13
Dear Sanderj,
I pressed Alt+Ctrl+F1 and logined in terminal mode
I found the following errors:
unable to read /etc/apt/apt.conf.d/ - DirectoryExists (2: No such file or directory

any help?

> **sanderj said:**
> Ubuntu 10.10? You now that that version is not supported anymore? See [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases#Table_of_versions)

I checked my own Ubuntu:

```
sander@flappie:~$ locate tunables | grep global
/etc/apparmor.d/tunables/global

sander@flappie:~$ dpkg -S  /etc/apparmor.d/tunables/global
apparmor: /etc/apparmor.d/tunables/global
```

... so: remove and then re-install "apparmor" and see if the error goes away.

---

### Post by sanderj on 2013-03-13
Sounds like a very problematic system. And unsupported Ubuntu version.

Advice:
Boot from a CD/USB with a current Ubuntu version and save what you want to save
Then install a fresh, supported Ubuntu


HTH

---

