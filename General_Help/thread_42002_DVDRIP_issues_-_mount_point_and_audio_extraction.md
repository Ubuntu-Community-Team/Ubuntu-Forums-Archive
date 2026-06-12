---
title: "DVD::RIP issues - mount point and audio extraction"
date: 2005-06-15
forum: General Help
---

### Post by Nick Post on 2005-06-15
I"m trying to rip the audio tracks off a DVD.  But I"m having issues.  The first issue, it's always there.  Upon pressing the Read DVD TAble of Contents button, i get:
[INDENT]
Failed to copy the IFO files, vobsub creation won't work properly
(Did you specify the mount point of your DVD drive in the Preferences?)
Ther error message is:
Failed to mount DVD at /cdrom (mount: No medium found)[/INDENT]

This is, however, after it's actually already gotten the data off it.  There is the green arrow thing cdrom, and I was thinking telling it to look at cdrom1 (the dir that the DVD is mounted to) but no go.  

I"m not sure if this is a big deal or not, but I'm not fond of error messages and I'm ignorant of how to fix this.

Problem 2 is actually actively bugging me.  When I select the track that I want to extract the WAV from and pick "Operate/Create Wav from selected audio track" I get an error.  (unfortunately I can't seem to copy and paste the error message, so I'll type it in, like I did the one above)

[INDENT]Job 'Dumping WAV - title #2, track #0' failed.

Executed command: mkdir -p /home/mark/TMBGABCs/avi/002 && dr_exec transcode -a 0 -y null,wav -u 100 -o /home/mark/TMBGABCs/avi/002/TMBGABCs-002-00.wav -x null -i /home/mark/TMBGABCs/vob/002 && echo DVDRIP_SUCCESS

Last output was:

transcode v0.6.14 (c) 2001-2003 Thomas Oestreich, 2003-2004 T. Bitterberg
[transcode] critical: invalid filename of host "/home/mark/TMBGABCs/vob/002"[/INDENT]

And it must be noted that when I look in my TMBGABCs dir there is only an avi and tmp directory.

When checking for dependencies of the program, I'm only missing subtitle2pg (which shouldn't matter in this case), dvdrecord (ditto), and xine (I use mplayer).

Any ideas?

Or can someone suggest a different program besides DVD::RIP for this?

Mucho thanks in advance.  You are my little gods.  *bow* *bow*

---

### Post by Nick Post on 2005-06-16
Answering my own question (on the forum for future seachers) part I

I found this thread:

[http://ubuntuforums.org/showthread.php?t=32665&highlight=dvdrip+mount+point](http://ubuntuforums.org/showthread.php?t=32665&highlight=dvdrip+mount+point)

Which basically says, yeah, that error message about the mount point, uh, ignore that.

Now to get to the real meat of the matter, getting those wavs off.

---

### Post by Nick Post on 2005-06-16
Also, looks to me like it's not creating the /vob/002 directory?

---

### Post by Nick Post on 2005-06-17
Answering my own question part II

Rip it first, then extract the wav.

(thanks for nothing guys)

---

