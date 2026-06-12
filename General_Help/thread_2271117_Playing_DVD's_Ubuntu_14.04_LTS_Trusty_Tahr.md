---
title: "Playing DVD's Ubuntu 14.04 LTS Trusty Tahr"
date: 2015-03-27
forum: General Help
---

### Post by mdavis1231 on 2015-03-27
I can play DVD's in my Ubuntu 14.04 LTS Trusty Tahr, so I know that I have all of the correct codecs installed, however, it will only play one DVD.  If I insert another DVD, it won't do anything unless I restart my computer.  What's wrong? :confused:

---

### Post by yancek on 2015-03-27
If you can see an icon for the DVD in the left panel, right click it and select to "Safely Remove" or "Eject" it before putting in another DVD.

---

### Post by mdavis1231 on 2015-03-27
I apologize, I didn't mention that I'm using Gnome-Session-Fallback.  How would I do that in Gnome-Sesson-Fallback?

---

### Post by mc4man on 2015-03-27
> **mdavis1231 said:**
> I apologize, I didn't mention that I'm using Gnome-Session-Fallback.  How would I do that in Gnome-Sesson-Fallback?

Try inserting a dvd, quick play for a few sec.'s, then in your file manager's sidebar > r. click on > eject. Then see if a different dvd is playable.

---

### Post by mdavis1231 on 2015-03-28
OK, I inserted the DVD, the menu came up, I ejected through Totem File>Eject, and was able to play another DVD.  Thanks!!!  Question...I have 2 DVD's that for some reason when I put them in, all it will do is open a folder with a file in it that says "VIDEO_TS".  The videos will play in Windows 7 Professional, but not in my Ubuntu 14.04 LTS Trusty Tahr. I'm noticing that many, many others are having problems playing DVD's on their 14.04 LTS also.  Is there another package that I need to install?  When I run "sudo regionset" in terminal, I get this:

regionset version 0.1 -- reads/sets region code on DVD drives
ERROR: Could not open disc "(null)"!
Please ensure there is a readable CD or DVD in the drive.

I would like to be able to play ALL DVD's in my Ubuntu 14.04 LTS Trusty Tahr.

---

### Post by mdavis1231 on 2015-03-28
Does anyone have any ideas what packages I might be missing, or what I should do to get my Ubuntu 14.04 LTS to play these videos?

---

### Post by Kaabi on 2015-03-29
Have you tried opening the dvd by first opening VLC/Totem and using the app to open the DVD?

---

### Post by coldraven on 2015-03-29
I had three brand new DVDs that would not play. After I cleaned the drive's lens two of them would play. I had to clean the lens again to get all three playing. I smoke and have pets that shed hair everywhere, this is a bad combination for DVD drives :(
There could be just one speck of dust on your lens, one DVD will cope with the errors but another will not. YMMV

---

### Post by maclenin on 2015-03-29
**mdavis1231!**

I have had similar (as well as many other) issues with dvds + *buntu over the years and have, generally, been able to resolve them using a combination of the following:

1. Install vlc
```
sudo aptitude install vlc 
```

2. Install audio / video codecs
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Additionally, with regard to your particular (regionset) issue, take a peek at this:

3. Troubleshooting
[http://ubuntuforums.org/showthread.php?t=2231976](http://ubuntuforums.org/showthread.php?t=2231976)

Good luck!

---

### Post by mdavis1231 on 2015-03-30
Here's a really weird thing.  I installed VLC player (which i don't like), and all of a sudden the DVD started spinning, and showed up in Totem.  I clicked on one chapter, then it froze.  Then I restarted my computer, and right back to the same old thing.  Something's missing, I just can't figure out what it is.

---

### Post by mc4man on 2015-03-30
1. regionset - if this is the same drive used with windows then it would have already had a region set. To note - 
sudo is not required to run regionset but a disc must be in the drive before running & you need to specify drive, ex.'s
```
regionset /dev/sr0
or if above isn't the drive
regionset /dev/sr1
```
2. the problem dvd(s) may have structure protection. In some protections you'd need to either specify the 'real' title number, others you may need start without menus, maybe a couple can't be played in linux.

To test without menus one - 
insert disk, let drive settle, close any pop up or player
delete ~/.dvdcss folder
open vlc > Media > Open Disc > select DVD & enable the  'No disc menus' option. Then click on Play button & see.

If you want to mention the name of some of these problem discs then *may* be able to check out later myself

---

