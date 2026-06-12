---
title: "Disable on boot &quot;syncronize time with ubuntu.org&quot;"
date: 2005-10-30
forum: General Help
---

### Post by skonvolt on 2005-10-30
How I can disable on boot "syncronize time with ubuntu.org" ???
It take a lot of time, and it isn't so important.. :( 
Thanks a lot !!! ;)

---

### Post by Hyun on 2005-10-30
```
sudo update-rc.d -f ntpdate remove
```
or install [**BUM - Boot Up Manager**]("http://www.ubuntuforums.org/forumdisplay.php?f=75")

---

### Post by skonvolt on 2005-10-30
Thanks Thanks Thanks !!! :d :d :d

---

### Post by Doc.Caliban on 2005-11-02
[QUOTE=Hyun]```
sudo update-rc.d -f ntpdate remove
```[/QUOTE]

Question #1

Can I assume that this doesn't disable time synchronization completely?  Just the boot sync?  That's my assumption since that was the requested fix, but I want to be certain before I run the command.  I too would like to disable boot time synchronization while still allowing automatic synchronization at other times.


Question #2

Are there advanced options for telling the service exactly when or how often to synchronize?

Thanks in advance, these forums have made all the difference for me in switching to Linux.

-Doc

---

### Post by mykey on 2005-11-02
you do not get rid of it installing BUM - but - if you move the script 'ntpdate' away from the /etc/init.d folder, it will not get executed and you can always move it back there anytime again

---

### Post by niko_ on 2005-11-02
Doc.Caliban you could edit your crontab (under root) for synchronizing at specific time
check out [http://www.hmug.org/man/5/crontab.php](http://www.hmug.org/man/5/crontab.php) or 'man crontab'.

> sudo echo "5 0 * * *       /etc/init.d/ntpdate start;" > ntc;
sudo crontab ntc && rm -rf ntc;

example this would synchronize your time everyday 5min after midnight

---

### Post by jvictor on 2005-11-03
Install bum , that gives u  many options which u can use to config ur boot up. At least it worked for me :)

---

### Post by Xian on 2005-11-03
[QUOTE=Doc.Caliban]Can I assume that this doesn't disable time synchronization completely?  Just the boot sync? [/quote]
That is correct. You would need to remove the ntpdate package to disable the ability to time sync completely. There are other debian applications like ntp-simple and chrony that perform similar functions.

[QUOTE=Doc.Caliban]Are there advanced options for telling the service exactly when or how often to synchronize?[/QUOTE]
When and how often is the responsibility of cron. Where is found in the /etc/default/ntpdate file. There you can list addtional NTP servers and choose more local options.

---

### Post by vassie on 2005-11-03
[CENTER][LEFT][FONT=Verdana][COLOR=Black]I'd say a better way would be to....[/COLOR][/FONT]

```
sudo gedit /etc/default/ntpdate
```

[FONT=Verdana][COLOR=Black]and comment out [/COLOR][/FONT][COLOR=#808080]*[FONT=Verdana][COLOR=Black]NTPSERVERS="ntp.ubuntulinux.org"[/COLOR][/FONT]*[/COLOR]

[COLOR=#808080]*[FONT=Verdana][COLOR=Black]Ben[/COLOR][/FONT]*[/COLOR]
[/LEFT]
 [/CENTER]

---

### Post by brentroos on 2005-11-25
*

---

### Post by slimvad on 2006-03-28
[QUOTE=Hyun]```
sudo update-rc.d -f ntpdate remove
```[/QUOTE]
```
sudo update-rc.d ntpdate defaults
```
Is it ok to restore it this way when/if needed?

---

