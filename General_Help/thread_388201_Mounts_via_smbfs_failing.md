---
title: "Mounts via smbfs failing"
date: 2007-03-19
forum: General Help
---

### Post by FastZ on 2007-03-19
Alright, I ran into a bit of a problem yesterday with mounting a few network shares via smbfs.  The two shares have been mounting successfully at startup for ages now but all of a sudden yesterday, they just went kaput and died on me.  I have an entry in /etc/fstab so that they will mount automagically.  

```

//192.168.1.149/Music  /media/Music  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

//192.168.1.149/ftp  /media/FTP  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

```Those two network shares no longer mount up during startup like they used to and anytime I try to manually surf into the /media directory, it takes forever and a day for anything in that directory to show up in Nautilus.  I have tried mounting via sshfs via command line using the following commands:

```

sshfs 192.168.1.149:/ftp /media/FTP

```and 
```

sshfs 192.168.1.149:/Music /media/Music

```which seem to work just fine _sometimes_ but whenever they mount and I double-click the icon that comes up on the desktop, it just sits there and never opens the share.  When I go to the /media directory, the folder icons for both /Music and /FTP now show up with a text document type icon instead of the regular folder icon.  When I click on these files to open them, they just disappear.  WTF?  

I dont know what the deal is and mounting a network share like this is the only way I could get Rhythmbox to ever play music directly from my server.  This sucks.  Any of your guys have any ideas at what might be going on?

Oh and I restarted the computer and when I logged back on, my DST settings had gone kaput too... The time had changed when it was supposed but when I logged in yesterday, the time had gained another hour...when it wasnt supposed to.  I just manually adjusted that for the time being.

Thanks for your help.  I know that's a lot but I cant figure out what's wrong and I've tried everything I know how to do, which really aint too much.

---

### Post by H3g3m0n on 2007-03-19
Try 'cifs' instead of 'smbfs' its the newer replacement.

I just replied to a similar thread here, so try some of that:
[http://www.ubuntuforums.org/showthread.php?t=388232](http://www.ubuntuforums.org/showthread.php?t=388232)

Also a howto here:
[http://www.ubuntuforums.org/showthread.php?t=375563&highlight=samba+automount](http://www.ubuntuforums.org/showthread.php?t=375563&highlight=samba+automount)

---

### Post by FastZ on 2007-03-19
Ok, I followed the examples in that first link.  I copied the example /etc/fstab entry verbatim (put my server info and username and password in the /etc/credentials file along with the shares I have on my server) and upon bootup, it still doesnt automount those two shares.  I tried to sudo mount -a them and that gave me the following error.

```

mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```I thought maybe it was because the two mount points were owned by root or something on my system here so I chowned them to my username and tried sudo mount -a again with the same luck.

This is my /etc/fstab entry for cifs
```

//192.168.1.149/Music /media/Music cifs      auto,user,credentials=/etc/smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777     0 0
//192.168.1.149/ftp /media/FTP cifs      auto,user,credentials=/etc/smbcredentials,iocharset=utf8,file_mode=0777,dir_mode=0777     0 0
```

---

### Post by Wicca on 2007-03-20
I had the same problem when I upgraded from Dapper to Edgy. My networkshare, mounted in fstab, didn't work anymore. Besides that, Nautilus was incredible slow and even froze completely when browsing to /media.
Maybe you can try what I did.

The problem line in fstab was this one:
```
/192.168.0.10/files /media/dione smbfs username=default,password=default,umask=007 0 1
```
Nothing wrong with that I thought, it has been working for months, but when I removed it from fstab and restarted, Nautilus worked normal. When I added the line again, Nautilus froze again entering /media.
Then I removed the line again and tried to manually mount my networkshare:
```
mount -t smbfs //192.168.0.10/files /media/dione
```
and it worked: I could browse my networkshare and Nautilus was fast and fresh again.

So as a workaround,  I added this same line to /etc/rc.local to make sure it is initiated at boot time. Now my networkshare is automatically mounted at startup, I can browse and play music from it as worked before.
This is the line in /etc/rc.local: (your options may be different than mine)
```
mount -t smbfs //192.168.0.10/files /media/dione -o fmask=777,dmask=777
```

Still do not understand why it stopped working in fstab :confused:

---

### Post by bonustracks on 2007-03-27
Same problem here.

---

### Post by FastZ on 2007-04-21
Well, I never did get that problem figured out in Edgy.  I upgraded to Fiesty the other day and just this morning tried to mount those shared drives on here via fstab.  I copied the exact same entry as I had in Edgy's fstab and, well, works like a charm after I installed smbfs.

```
 //192.168.1.149/Music  /media/Music  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0

//192.168.1.149/ftp  /media/FTP  smbfs  guest,uid=1000,iocharset=utf8,codepage=unicode,unicode  0  0
```

That's the same entries I used to begin with before, and they seem to work very nicely in Fiesty.  So I dunno what the problem was with my Edgy install.  Maybe because I had a lot of other stuff all going on at the same time.  I had tinkered around so much with that install that things were starting to just not work anymore and slow down considerably.  I think I'm done playing and will eventually do all the tinkering on a machine that I dont rely on to use everyday.

---

