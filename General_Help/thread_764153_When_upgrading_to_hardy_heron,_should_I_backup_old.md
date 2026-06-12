---
title: "When upgrading to hardy heron, should I backup old files?"
date: 2008-04-23
forum: General Help
---

### Post by AlexLinuxUser101 on 2008-04-23
I am planning to upgrade to hardy heron when it comes available to us through the update manager, and I was wondering if I should backup my music and stuff.  Is it a safe procedure or is it generally pretty risky?  Documents, music, videos, etc.  Should they be backed up?  How about settings?  For example, firefox settings, compiz settings, etc.  I know I can't back them up, but will I have to reenter them?  

Most importantly I really can't afford to lose all of my documents and I can't easily backup my files, so if someone knows whether I need to please tell me.  Now that I think of it, though, I have an existing partition I use for windows (a crack which I think may have expired now as the crack didn't really work) which I can access from my ubuntu partition.  Should I just put my files on that, and will the ubuntu upgrade affect that?

I am pretty excited for the new upgrade.  While I'm here, I've been having a lot of problems with the current ubuntu.
- Firefox freezes REALLY EASILY.  Like, if there are animations or videos on a page it can easily.  Alternatively, it freezes when I open like 30-40 tabs at once (I suppose I shouldn't expect it to work, but it's nice to go on a forum and open up all the threads I want to look at as opposed to one at a time).  
- Rhythmbox randomly shuts down sometimes.  It's just playing music and then just... shuts down.

That's all I can think of right now.

Thanks for your help.

---

### Post by p_quarles on 2008-04-23
The upgrade procedure is safe, but having important documents that aren't backed up isn't. Find a way to make backups, or expect to lose your data somehow or another.

---

### Post by olavjunior on 2008-04-23
agree! It will prob be ok, but if you're not to familiar with Ubuntu a backup is always safe (your disk may crash one day anyways...) But really, an update will leave all your files and settings as is, so no need for backing any of those up! But a fresh install is usually the best and most stable (but I'm on an upgraded hardy myselfe, and it's good) update is the most easy! Even though a fresh install also keeps your files in an .old folder or somehting like that if I don't remember it wrong..

---

### Post by warp99 on 2008-04-23
> **AlexLinuxUser101 said:**
> I am planning to upgrade to hardy heron when it comes available to us through the update manager, and I was wondering if I should backup my music and stuff.  Is it a safe procedure or is it generally pretty risky?  Documents, music, videos, etc.  Should they be backed up?  How about settings?  For example, firefox settings, compiz settings, etc.  I know I can't back them up, but will I have to reenter them?  

Most importantly I really can't afford to lose all of my documents and I can't easily backup my files, so if someone knows whether I need to please tell me.  Now that I think of it, though, I have an existing partition I use for windows (a crack which I think may have expired now as the crack didn't really work) which I can access from my ubuntu partition.  Should I just put my files on that, and will the ubuntu upgrade affect that?

I am pretty excited for the new upgrade.  While I'm here, I've been having a lot of problems with the current ubuntu.
- Firefox freezes REALLY EASILY.  Like, if there are animations or videos on a page it can easily.  Alternatively, it freezes when I open like 30-40 tabs at once (I suppose I shouldn't expect it to work, but it's nice to go on a forum and open up all the threads I want to look at as opposed to one at a time).  
- Rhythmbox randomly shuts down sometimes.  It's just playing music and then just... shuts down.

That's all I can think of right now.

Thanks for your help.

These are the items that you should back up:

1) Your home directory with all of your local settings
2) You xorg.conf file since Hardy may overwrite this with a 'minimal' xorg.conf file that has been troublesome for some users.
3) Any custom conf files that may be overwritten during the upgrade.

You can copy the files over to a separate partition if you like, there's no need to move them off the drive. If there's the unlikely event of a catastrophic failure with the upgrade you can reinstall and copy over your home directory, xorg.conf, and any custom conf files to restore you settings.

---

### Post by chrisccoulson on 2008-04-23
What warp said, but in addition - I would recommend to back up the entire contents of /etc because this is where most custom system-wide configurations are likely to be, and it takes up hardly any space.

I'm actually super cautious and back up my entire filesystem by putting it in to a tar file, copying it in to /home and then doing my usual backup of /home by synchronising it to my external USB hard disk. This is not necessary in most cases though and might be considered a bit overkill

---

### Post by ravenus on 2008-04-24
What is the simplest method of backing up settings in Ubuntu when doing a fresh install of a newer version? Is there any backup utility which will make one backup dump file that the new install can read from?

---

### Post by faithsnathan on 2008-04-24
> **chrisccoulson said:**
> I'm actually super cautious and back up my entire filesystem by putting it in to a tar file, copying it in to /home and then doing my usual backup of /home by synchronising it to my external USB hard disk. 

[FONT=Trebuchet MS][SIZE=4][COLOR=DarkRed]So, if just make my home directory or my documents into a .tar file, and copy that to my 4GB SD card, would that be a good enough way to back up my documents?  I was thinking of doing this to backup my files in order to do a fresh install of Heron (I currently have Gibbon).  Does anyone know if this method would work once I'm on the other side and want to open the tar files and bring my folders out into the light?[/COLOR][/SIZE][/FONT]
Edit:  Yes, backing up my documents by right click, make archive, and choosing tar worked just fine.   I got anxious and tried it anyway.


> **ravenus said:**
> What is the simplest method of backing up settings in Ubuntu when doing a fresh install of a newer version? Is there any backup utility which will make one backup dump file that the new install can read from?

[FONT=Trebuchet MS][SIZE=4][COLOR=DarkRed]From my research, there are several choices for backing your stuff in Ubuntu:

[sbackup]("http://sbackup.sourceforge.net/HomePage")
[rsync ]("http://samba.anu.edu.au/rsync/")(and it's graphical front-end [grsync]("http://www.opbyte.it/grsync/"))[/COLOR][/SIZE][/FONT]

---

### Post by ravenus on 2008-04-26
Thanks for that. I looked for sbackup but the sourceforge site was down. Anyway, turns out I didn;t need it so much since I had a separate Home directory.

---

