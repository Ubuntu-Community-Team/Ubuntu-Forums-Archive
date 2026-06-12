---
title: "Can't mount dvd drive after system update"
date: 2007-02-22
forum: General Help
---

### Post by kopikat on 2007-02-22
After running an automatic update via Synaptic I can't mount my dvd drive no more. Not only it doesn't automount as before, but I can't mount it by means of the command line either and the fstab entry has been erased too. Any ideas on why this happens? 
Ubuntu is really great, but I'm getting pretty tired of the PUTD: Post Update Traumatic Disorder. The X server got screwed twice and now this! Come on people, I won't be able to convert my friends to Linux with that kind of behavior! I friend of mine already switched back to Winshit because of this.

---

### Post by pay on 2007-02-23
You'll have to add an entry to your fstab. ```
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```obviously change /dev/hdc to your cdrom.

---

### Post by yoda2031 on 2008-02-05
Google brought me here and I didn't bother checking the date, so sorry if I'm bumping an age-old topic - but most forums agree that it's better to find a topic with your precise query in and bump, even if it's millenia old, than create an entirely new topic devoted to the same thing.  Anyway, I couldn't find any specific help about this on google or these forums so here we go.

I'm having this same issue, post-update, on a Hardy build that I'm desperately trying to get rid of.  The problem is that I have 4.1GiB of data that I /must/ back up.  This means either sending it down the line to a friend (which would require an insane amount of time and a very trustworthy friend, of which I have neither - most of my friends are running highly insecure Windows boxes which are simply inadequate for this data's nature).  OR I could back it up onto DVD.  I have 16 DVD-RWs sitting here and a compatible internal DVD Writer, but Ubuntu Hardy flatly refuses to mount it (perhaps it's not ready to give up the ghost, as it is probably well aware of my intention to replace it with a more stable version of Ubuntu, if not a completely different distro; although I must say Ubuntu has been the best OS I've experienced in my relatively short Linux life (of 1.5 years [1 year 6 months, for the digitally inept]).  Anyway, the point is I've ls'd my /dev directory and I have no clue what my DVD writer would be called.  The one mentioned in the example fstab file above does not appear on my list, so there's no point trying that.  I know what a few of the devices are, and some of them bewhilder me, but none stand out as having 'dvd' or anything easily recognisable like that in them.  If someone could get back to me here I'd love it, and if someone is feeling particularly helpful, emailing [email]yoda2031@gmail.com[/email] will mean I get the solution a lot faster because gmail has the handy feature of changing the title when I get mail, so I am immediately aware of such an event occurring.  Thank you in advance,

Yoda

---

### Post by andydread on 2008-05-01
Same problem here on new installs of Hardy. Gutsy worked fine with this hardware.   I have spent the whole week on this and still cannot under ANY circumstances get several laptops and a PC to mount ANY Unencrypted DVD. Video or DATA.  Do they actually do any kind of quality control ?  How can u make such a big release with such obvious SHOW STOPPING bugs?  It would have been better to DELAY the release rather than let loose something so obviously broken.  The forums and launchpad are falling over with this problem and it seems the devs are just totally unaware of the seriousness of this issue.  Where is Mark Shuttleworth in all of this? It needs to be fixed NOW. 

```
Unable to mount location. No media in drive.
```

---

### Post by andraycho on 2008-05-01
I had a same problem and fixed the mounting problem by changing following line in the /etc/fstab.

From
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

To:
/dev/scd1        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I guess Hardy didn't detect the device path for the DVDRW.

Now, DVD Read is fine but DVD Write is not working yet.

---

### Post by andydread on 2008-05-02
THis is what I have in my fstab file.  
/dev/scd0 is the DVDrom/CDRom drive
/dev/Scd0 is the CDRW

/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0

the DVDrom drive will only mount CDs no DVDs data or otherwise.

---

### Post by pcmantinker on 2008-05-03
Try this:
```

/dev/cdrom0 /media/cdrom0 auto ro,noauto,user,exec 0 0
/dev/cdrom1 /media/cdrom1 auto ro,noauto,user,exec 0 0

```
auto lets Ubuntu detect the filesystem of the disc when it's inserted. ro mounts the disc as read only. The other stuff following I am unsure of what it is exactly. I am still learning how to configure Ubuntu fully. Hopefully this will work.

---

