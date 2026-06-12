---
title: "Automount and not existing Keys"
date: 2021-12-04
forum: General Help
---

### Post by alain.roger on 2021-12-04
Hi,

In the past I used /etc/fstab to mount my NAS shares, but now I use autoFS and it works great.

Analyzing my logs I discovered that for some unknown reasons my ubuntu still searching for those Keys I used in /etc/fstab and poluate my logs with such messages:
```
déc. 04 10:21:08 PC0001 automount[1788]: key "Business" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "Applications" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "Tempo[2TB]" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "qnap" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "wd-backup-6tb" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "wd-backup-4tb" not found in map source(s).
```

None of these keys are in my fstab file anymore nor in my autoFS configuration, so from where are they coming ? I even did not use them in my autoFS configuration, so where fstab stored them?

when I type: service autofs status, this is the report:

[FONT=monospace]
```
[COLOR=#54ff54]**&#9679;**[/COLOR][COLOR=#000000] autofs.service - Automounts filesystems on demand [/COLOR]
     Loaded: loaded (/lib/systemd/system/autofs.service; enabled; vendor preset: enabled) 
     Active: [COLOR=#54ff54]**active (running)**[/COLOR][COLOR=#000000] since Sat 2021-12-04 17:05:39 CET; 24s ago [/COLOR]
       Docs: man:autofs(8) 
    Process: 1627587 ExecStart=/usr/sbin/automount $OPTIONS --pid-file /var/run/autofs.pid (code=exited, status=0/SUCCESS) 
   Main PID: 1627588 (automount) 
      Tasks: 4 (limit: 38325) 
     Memory: 1.4M 
        CPU: 16ms 
     CGroup: /system.slice/autofs.service 
             &#9492;&#9472;1627588 /usr/sbin/automount --pid-file /var/run/autofs.pid 

déc. 04 17:05:39 PC0001 systemd[1]: Starting Automounts filesystems on demand... 
déc. 04 17:05:39 PC0001 systemd[1]: Started Automounts filesystems on demand. 
[COLOR=#ff0000]déc. 04 17:05:43 PC0001 automount[1627588]: key "wd-backup-4tb" not found in map source(s). 
déc. 04 17:05:43 PC0001 automount[1627588]: key "wd-backup-6tb" not found in map source(s). 
déc. 04 17:05:43 PC0001 automount[1627588]: key "qnap" not found in map source(s). 
déc. 04 17:05:44 PC0001 automount[1627588]: key "Tempo[2TB]" not found in map source(s). 
déc. 04 17:05:44 PC0001 automount[1627588]: key "Applications" not found in map source(s). 
déc. 04 17:05:44 PC0001 automount[1627588]: key "Business" not found in map source(s).
```[/COLOR]


[/FONT]The keys in red lines do not exist anymore, but I do not know in which configuration file or subsystem they are stored. They are not in /etc/fstab nor in auto.mnt or auto.master files

thx.

---

### Post by TheFu on 2021-12-05
Did you happen to use a "mark permanent" in a file manager?
There are some systemd Unit file refresh commands ... if systemd decided to "help".  Those are automatically created if you use the "automount" option in the fstab. Perhaps they are left over somewhere?

sudo systemctl daemon-reload
sudo systemctl stop {name of mount}.automount
sudo systemctl mask {name of mount}.automount

For example, I have a /misc/D mount (it is a CIFS mount from a Windows box).  The name of the automatically created unit file is misc-D.automount.  It was cleaned up (somehow) when I removed that mount line from the fstab.

I'm more inclined to thing it is a GUI program setting. Check the file manager?

---

### Post by alain.roger on 2021-12-05
I use Dolphin as i have KDE installed.

This was my second guess, so I checked Dolphin but I have nothing permanent mount there. Only the actual and valid Key/shared driver from NAS. I do not have anymore nautilus so noway to have them from there.


I searched on web and I saw that I'm not the only one to have such issue with system trying to mount former or non existing key/driver/mounting points.
But nowhere I could find a solution.

What I do not understand it's that such keys I used for my fstab and I firstly checked fstab, but there are removed from file content.
So it's like system kept a trace of such fstab mounting points and never removed them. This is weird as I do not know where such keys could be kept/stored.

---

### Post by TheFu on 2021-12-05
I'd use '**locate**' to search for files on the system with those names.  Did you look for all the .automount files on the box?  I have some in /lib/systemd/system/ and for some snaps (ARGGGGGGGG!).

The term "key" isn't clear in this context. Can you please clarify?  Local connected storage wouldn't be using Kerberos to my knowledge. That's the only "key" I can imagine and they are typically called "tokens" in the client/server connection .. after the key exchange happens.

---

### Post by alain.roger on 2021-12-05
I'm currently trying to find a file in my whole / and /home/alain having content with one of the non-existing key..

So for now I typed:
```
[FONT=monospace][COLOR=#000000]sudo grep -rnw 'wd-backup-6tb'[/COLOR][/FONT]
```

I know that automount (autoFS) file are auto.mnt, auto.master and I checked also the auto.deny, auto.allow, auto.misc, but no file includes one of my non-existing key :(

command locate search for file having the file name equal to non-existing key, AFAIK.
My first try was to find in my profile directory some files that could include as content such non-existing key.

I did a simple test. I commented the last line (I added manually before)  of my /etc/auto.master
```
#[FONT=monospace][COLOR=#000000]/mnt /etc/auto.mnt --ghost,--timeout=30[/COLOR]
[/FONT]
```

Since that my log is NOT ANYMORE populated every minute by :
```
déc. 04 10:21:08 PC0001 automount[1788]: key "Business" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "Applications" not found in map source(s)
déc. 04 10:21:08 PC0001 automount[1788]: key "Tempo[2TB]" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "qnap" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "wd-backup-6tb" not found in map source(s).
déc. 04 10:21:08 PC0001 automount[1788]: key "wd-backup-4tb" not found in map source(s).
```

However my current and valid shared directories from my NAS are not automount anymore.

Here I can see 2 bugs:
1. my logs are populated every minute, while in my auto.master I stated every 30s
2. the content of my /etc/auto.mnt file do no include any of these non-existing key

Here is the content on my /etc/auto.mnt file:
```
[FONT=monospace][COLOR=#000000]qnap-home                       -fstype=nfs,rw          qnap:/homes/alain [/COLOR]
qnap-ext-backup-disk-4tb        -fstype=nfs,rw          qnap:/nas-backup-4tb 
qnap-ext-backup-disk-6tb        -fstype=nfs,rw          qnap:/nas-backup-6tb 
qnap-changing-data              -fstype=nfs,rw          qnap:/changing-data 
qnap-static-data                -fstype=nfs,rw          qnap:/static-data[/FONT]
```

---

### Post by alain.roger on 2021-12-08
I want to share here my conclusions about autoFS and automount, as it could help other users to find out a solution if they did the same as me (mount other internal disks or NAS shared directories in /mnt directory using fstab).

I just performed a simple test by creating a directory /misc and change my auto.master added line with /misc as root directory for NAS shared directories (instead of /mnt).

Since them automount do not populate my logs with former mounting points / non-exisiting keys / former keys from fstab.

Therefore, my user desktop starts a lot faster.

So it's clear that autoFS keep track of former configurations file and keys, but till now I was not able to find where such files/configuration or keys are stored.

---

### Post by TheFu on 2021-12-08
autofs == automount.   It comes from the amd daemon (that's redundant) from the Unix world in the 1990s.  amd and autofs both mount and umount storage on-demand, when a process requests is.  This is typically used for any external-to-the-system storage, like NFS, CIFS, USB.  Things that aren't physically SCREWED into the system.  So an external array connected with SCSI or Infiniband (both use screws in their cables) wouldn't need autofs, but USB and any network storage would.

systemd added a "lite" capability to delay mounting using fstab entries, but wait until the storage was demanded, just like autofs does, however, the systemd version never umounts that storage (at least in my testing).  Once mounted, it remained mount until reboot or a manual umount happened.

SNAP WARNING
If you use snaps, there are only 3 places that snaps allows storage. These are hard-coded into the snap daemon. There doesn't appear to be any viable way to get around it, besides not using snaps.  Those 3 locations:
/home/
/media/
/mnt/
The first is the only one always available for all snap packaged programs.  In fact, if the HOME directory for the user isn't /home/, snap tools and packages will not run.
The other two locations are dependent on the snap packager to allow and users to enable.  The command to allow chromium access to these other two locations is
$ snap connect chromium:removable-media
So, for other snap packages, just change the "chromium" to the package name.  However, if the team responsible for creating the snap package didn't think our it, then that removable-media connection won't work.  This has been uncovered multiple times.  For example, I came across a video editor that didn't allow it.  Only videos in my HOME could be edited.  That's just crazy and I was never able to that program.

For some period of time, snap packages didn't support any network storage either.  I don't know the details about the fix, but I think NFS is supported now, but not for HOME directories. Having HOME directories on NFS is how enterprise teams work, so I'm a little perplexed by this. I'm also perplexed for why the location of a HOME directory in the system passwd DB isn't sufficient for snaps to allow the location.

I still don't know what "keys" are being discussed in this thread and would love an explanation.

---

### Post by alain.roger on 2021-12-11
Ubuntu use the term KEYS from mounting perspective to describe/name in fact mounting points. So if you have some folders in /mnt, the name of the folder is the mounting point, but for ubuntu it is also named KEYS.
In logs, ubuntu did not reference mount point as mounting points, but as keys.

Am I clearer now ?

---

### Post by TheFu on 2021-12-11
> **alain.roger said:**
> Ubuntu use the term KEYS from mounting perspective to describe/name in fact mounting points. So if you have some folders in /mnt, the name of the folder is the mounting point, but for ubuntu it is also named KEYS.
In logs, ubuntu did not reference mount point as mounting points, but as keys.

Am I clearer now ?

Yes. Thanks.  I think it is a translation thing.  I don't see any mention of "key" in my logs on any systems related to mounting and I've never heard it used in that way.  I can also understand why seeing a word that is also an English word would lead to assuming it is the same - so many words, especially around computing DO use the English word in many other languages.   Perhaps UUID or Label are the terms I'm used to seeing? You'd know better than me.  Just confusing for me with my limited language skills.

```
$ journalctl |grep mount |grep -i key
```
outputs nothing.  With out the grep for key , there are lots and lots of lines - mostly from lxd apparmor problems and a few around NFS/CIFS mounts. None of my USB connected storage use 'key'.

Languages are very interesting. Thanks again for helping me to understand better.

---

