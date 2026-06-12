---
title: "totem-xine busted in 5.04 Hoary?!"
date: 2005-03-29
forum: General Help
---

### Post by edm00se on 2005-03-29
Bare with me here. Compared to most of the people I know, I'm a bit of a n00b. I've been running Ubuntu for a while, as it's been the single most kind distro to me. Anywho, I had totem-xine working perfectly fine in Hoary, before the big update/upgrade about a week ago (approx. 21-March-2005). Since then, this past weekend, I've noticed that a movie I tried to watch (a backed up/burnt copy) began to become very choppy. I had backed it up about a year ago, so I thought maybe it was a bit of bad physical media. Then I realized that it was not limited to burnt DVD's.
  My store bought DVD's have the same problem. The weekend before last week's large update, I watched a newly bought DVD with no trouble (Evolution, starring David Duchovney and Orlando Jones, in case anyone's interested). Now, after that update, it's all funky. I hoped this past weekend's update would solve things. Not at all.
  This is the first I've had trouble watching a DVD in totem-xine. Could somebody please help out a poor, old business major?
  On a side note, I'm not exactly 100% a damsel in distress. Totem-xine is not the only player to have this problem. Mplayer and VLC also experience the same. My friend's Ubuntu-Hoary system has it even worse. Again, only when played from the physical DVD disc in the drive. DMA *is on*  for the optical drive.
  All help is appreciated and I would love not to try switching distro's again (watching movies is something of a must for me). Thanks in advance.

---

### Post by Nis on 2005-03-29
[QUOTE=edm00se]Bare with me here. Compared to most of the people I know, I'm a bit of a n00b. I've been running Ubuntu for a while, as it's been the single most kind distro to me. Anywho, I had totem-xine working perfectly fine in Hoary, before the big update/upgrade about a week ago (approx. 21-March-2005). Since then, this past weekend, I've noticed that a movie I tried to watch (a backed up/burnt copy) began to become very choppy. I had backed it up about a year ago, so I thought maybe it was a bit of bad physical media. Then I realized that it was not limited to burnt DVD's.
  My store bought DVD's have the same problem. The weekend before last week's large update, I watched a newly bought DVD with no trouble (Evolution, starring David Duchovney and Orlando Jones, in case anyone's interested). Now, after that update, it's all funky. I hoped this past weekend's update would solve things. Not at all.
  This is the first I've had trouble watching a DVD in totem-xine. Could somebody please help out a poor, old business major?
  On a side note, I'm not exactly 100% a damsel in distress. Totem-xine is not the only player to have this problem. Mplayer and VLC also experience the same. My friend's Ubuntu-Hoary system has it even worse. Again, only when played from the physical DVD disc in the drive. DMA *is on*  for the optical drive.
  All help is appreciated and I would love not to try switching distro's again (watching movies is something of a must for me). Thanks in advance.[/QUOTE]
 The problem is that DMA is not being enabled for DVD and CD-ROM drives.  You can try to enable DMA using hdparm:
```

sudo hdparm -d1 /dev/hdb

```
where hdb corresponds to your DVD drive.  Better yet look at /etc/hdparm.conf (I think that's the location since I'm away from my machine right now).  You can setup some rules to run during bootup to enable DMA there.

By the way, when is DMA going to be turned on for all drives in the kernel, developers?  I know there's a kernel option being enabled that is causing this problem.  Maybe there's a good reason (turing DMA on causes problems elsewhere).

---

### Post by edm00se on 2005-03-30
Okay, firstly, passing hdparm the -d1 /dev/hdc does make it work. My only question now is, how can I make that permanent and why was it that beforehand, I checked my hdparm.conf file and I was under the impression DMA was turned on?
  For reference, I checked after-the-fact and it was commented out, good ol' me. For other people: how I added this to the the /etc/hdparm.conf file was merely to paste the following into it:

command_line {
hdparm -d1 /dev/hdc
}

  Thanks a bunch!

---

### Post by c_dog on 2005-03-31
The hdparm.conf file in the /etc folder, like most *.conf files by default, is an example of some of the configuration parameters that can be used in the *.conf. So, all of the "examples" in that file are commented out. They may or may not be (could have very bad effects) the right setups for your harware. Problem is the hdparm.conf is (at least in Hoary) read before the ide cd moudules are loaded. You may need to copy or move the /etc/rcs.d/s07hdparm symlink to the start script in /etc/init.d to a start later in the boot sequence. Giving it a starting position of 50 or higher should work out okay `s50hdparm’.

---

