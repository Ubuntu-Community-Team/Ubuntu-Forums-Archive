---
title: "Nautilus AFP access stopped working"
date: 2019-01-08
forum: General Help
---

### Post by lou6 on 2019-01-08
I have regularly used Nautilus/AFP on my home office computer (running 18.04) to access a WD MyCloud until recently.  Now, Nautilus still connects to the NAS - I can see the files but cannot access them - can't start a video or play an mp3 - the player (smplayer) just hangs.  Strangely, my other machine (in another part of the house but also running Ubuntu 18.04) works just as well as it always has.  Obviously something has happened to the office machine but I have no idea what it could have been.

Where should I start looking?  All help and suggestions welcome...

---

### Post by lou6 on 2019-01-09
No takers on this one so far - perhaps not many users have noticed that when accessing a NAS through Nautilus the default access method in 18.04 is AFP.  I was surprised by it as well (I have always been a Samba fan).

---

### Post by him610 on 2019-01-09
Did not know what AFP was, so I had to search for it. Found this, [https://ubuntuforums.org/showthread.php?t=2368070]("https://ubuntuforums.org/showthread.php?t=2368070")
Maybe it will help.

---

### Post by lou6 on 2019-01-10
I did check avahi - it starts (as it should) at bootup.  Thanks for responding.

---

### Post by lou6 on 2019-01-11
In the process of trying to fix this I discovered some files in my Home Folder that were owned by Root.  Evidently this was caused by some changes I made to system files by using sudo -H nautilus (as a substitute for the late gksudo).  I chowned the files that I found back to $USER and have experienced no other weirdness except for the AFP problem.

I've searched for info about where AFP mounts the NAS but have so far come up empty.

Perhaps this new info will ring a bell for one of the smart Linux people out there to help me fix this small (but annoying) problem...

---

### Post by lou6 on 2019-01-16
Well, this is definitely not solved but I will close it anyway - sorry I could not get help from those more knowledgeable.

EDIT:  After closing this 2 weeks ago I decided to reopen because I still have not found a solution on other websites.  It seems that the main question to be answered is "Where does Nautilus 3.26 mount AFP shares (and Samba shares)?".  If I had the answer to this I could probably track down the problem.

Mount points for shares have moved around in almost every new LTS release and I'm at a loss to say where they are now.

Any help will be appreciated...

EDIT: 02/07/19

I checked the 'working' machine (the one that accesses the files correctly) and found that AFP has mounted the NAS in /run/user/1000/gvfs but on the 'non-working" one the mount is not there.  I've reinstalled Nautilus with no joy - perhaps I need to purge Nautilus completely and reinstall from scratch?  I don't know and would REALLY appreciate some smart Ubuntu users help...

---

### Post by lou6 on 2019-02-08
Problem solved - I ran across this thread [https://askubuntu.com/questions/996949/how-to-restart-gvfs](https://askubuntu.com/questions/996949/how-to-restart-gvfs) and discovered that I did not have gvfs-fuse installed.  I have no explanation as to how it became uninstalled (or if it was somehow never installed in the upgrade to 18.04) but NAS access now works on both machines.

---

