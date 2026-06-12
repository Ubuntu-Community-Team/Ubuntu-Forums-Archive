---
title: "Sound/Video/Data Issues with New Motherboard/Install"
date: 2007-09-24
forum: General Help
---

### Post by Overquoted on 2007-09-24
I first posted this problem in Absolute Beginner Talk, the wrong place.

Two weeks ago, I bought a new motherboard to replace one that I fried. It's an ASRock P4i65G (onboard video, onboard sound). Then I reinstalled Ubuntu.

After the installation, I installed some software and updated. Immediately after that, programs started taking 2-7 minutes to open. I didn't feel like looking for the cause (especially given how long it took to open ANYTHING), so I reinstalled a second time.

This time, no opening problems once I updated. However, now I was noticing two things. One, my sound is almost non-existant and controlled solely by PCM. Speaker volume and Master do nothing. I bypassed this after several days by fishing out some old, powerful speakers. But that hasn't changed the initial problem of the sound being so low that I didn't realize it was even there until I turned the PCM control to 100% on a loud video.

The second, larger issue involves missing data. During the first install, I can recall accessing my 80GB drive to play a file (I wanted to see if .mkv files would play correctly). Totem popped up with the codec error message of course, but then I got stuck in the second install. Well, after I installed Ubuntu and updated, etc..I attempted to access those files again, only to find everything missing. No, the drive wasn't wiped. The Windows and Program folders are intact, the boot sector is fine, etc. But specific folders are missing entirely. 68+ gigs worth, in fact. The Desktop folder is missing, as are my Anime folder and Music folder that were in the root directory (C/Anime, C/Music...or more accurately, sdc1/Anime). I tried running two Linux data recovery programs...neither found any data.

Now, I know I didn't manually delete (even if I had, they'd have ended up in the .Trash folder...which is also missing, now that I think about it). Nor did it get wiped during install (if that were the case, the old Windows XP install would be screwed up, too). Also, since I didn't overwrite the data...it should still be there, in some form or another.

This might've had something to do with enabling write support under NTFS-3g. It's possible I did it on the first install (though I doubt I had the time), but I definitely did it with the second...but only after I noticed the problem, I think.

At some point, I'll buy another hard drive and install a Windows OS on it to see if the data is more recoverable from there. But for now, it's frustrating. I was going to back-up the data on the 80gb and reinstall XP so I could dual-boot. Now I'm just stuck with Ubuntu, which isn't enough thanks to two or three programs that won't run under Wine.

Now for the third problem. Those .mkv files I wanted to play? Major issue playing them. Under XP, even running Style XP and several programs, I never had trouble with .mkv. Not once. But on Ubuntu...well, when I play them, Ubuntu seems to think I'm maxing out my CPU (which is 2.7ghz). VLC will skip entire scenes while Totem will skip frames (giving the video a jerky appearance). Totem will also show a weird bright neon (almost metallic) green in the background of the video. Occasionally a .mkv file will crash the apps entirely.


If I can't get at least the video and sound issue solved, then I'll wipe this drive and install a Windows OS on it. The question is...can I back-up Ubuntu and reinstall it at a later date (even after a wipe)? That way, regardless of the outcome of my data recovery attempts, I can get Ubuntu back online and XP on the 80GB.

Sorry for the double-post. My old thread hadn't gotten a reply in two weeks.

---

