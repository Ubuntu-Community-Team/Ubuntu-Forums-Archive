---
title: "VDR strange message"
date: 2005-06-23
forum: General Help
---

### Post by mad_alfred on 2005-06-23
Hi,

i installed vdr using synaptic to view some FTA dvb satellite programs with my skystar 2..the card works perfectly since i scanned all transponders from root console :D

problem is that everytime i start vdr from root i receive this message:

```
root@ubuntu:/home/chris # vdr
vdr: sorry, I refuse to run with root privileges
```


..so i access console as a normal user and get this message:

```
chris@ubuntu:~$ vdr -c DIR
vdr: can't access video directory /var/lib/video.00
```

now..i've checked the directory and it exists!

```
root@ubuntu:/var/lib # dir
acpi-support  dhcp3           kdm              sgml-base        vdr
alien         discover        logrotate        slocate          video
alsa          doc-base        lsb              snmp             video.00
apt           dpkg            misc             synaptic         xfree86
aptitude      emacsen-common  mozilla-firefox  ucf              xkb
binfmts       fontconfig      mysql            update-manager   xml-core
cups          gdm             mythtv           update-notifier
defoma        gstreamer       scrollkeeper     urandom
root@ubuntu:/var/lib # cd video.00
root@ubuntu:/var/lib/video.00 #



```

now...what shall i do? please help, the only meaning i've got for using windows is that i can watch tv with my card, though i can feel i'm so close reaching the same goal with linux!

cheers,
chris

---

### Post by jarno on 2005-06-24
[QUOTE=mad_alfred]
..so i access console as a normal user and get this message:

```
chris@ubuntu:~$ vdr -c DIR
vdr: can't access video directory /var/lib/video.00
```
[/QUOTE]

Are the file permissions set so You can read the file with a regular user?

--
    /jarno

---

### Post by mad_alfred on 2005-06-24
[QUOTE=jarno]Are the file permissions set so You can read the file with a regular user?

--
    /jarno[/QUOTE]
 Now i changed owner from root console with chown -R , but when i start vdr nothing happens , it just hangs :(

---

### Post by blazko on 2005-07-21
Hi Chris,

Hope you solved your problem. If not, did you add your user to the "video" group (if not already is...)?

Greetings,
Timo

---

### Post by scorpio2002 on 2005-09-10
I'm having the same problem, I changed the owner of the directory and now when I run vdr it just hungs and there's no way to get it to work.... how to solve this?

---

