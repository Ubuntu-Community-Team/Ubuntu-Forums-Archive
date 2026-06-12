---
title: "Unable to boot edubuntu 7.10 gutsy gibbon"
date: 2007-12-15
forum: General Help
---

### Post by jblake on 2007-12-15
I downloaded Gutsy Gibbon 7.10 from Canonical UK - the image appears to have downloaded o.k. but have wasted 2 blank cdr's now. The usual run live cd/install menu appears but when trying to start after selecting all the Function key options, the Kernel fails to load. The CD-Rom whirrs away as if something is going to happen but it doesn't. I attempted 7.10 some months ago and had similar problems. There is nothing wrong with my burning equipment or ISO burning software from [www.NTFS.com](www.NTFS.com) as I have successfully burned Geubuntu using the same equipment and the same burn speeds. I am particularly interested in Edubuntu as learning software for my youngest daughter. Being someone who is actively involved supporting children with accessibility issues, I am also interested in Orca.
If anyone can advise of problems with the bootloader in the 7.10 image or other issues (note I downloaded the x86 not AMD64 version - the same results also happen on both x86 and AMD64 processors within the family.)
:confused::(:confused:

---

### Post by taurus on 2007-12-15
After you downloaded the ISO image, did you check the integrity of the file with md5?  Then, try to burn it at a slow speed as you can.  And when you boot from it, there is an option on the first menu that would allow to you check the CD.  Run it option to make sure the CD is all good to go.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck)

---

### Post by jblake on 2007-12-15
Thanks for such a quick response. I am afraid I did not download the md5 checksum at the time as I have never had problems with GNU/Linux *.iso's before - they have always worked. I presume they change on a daily basis or some timelapse basis - the md5 I downloaded from the md5's list from Ubuntu's download site do not match with Canonical (UK) Europe site. Are they different for each download site?
Have used the md5 graphical check program from Nullriver Software and they don't match. (Sigh!)
Does this mean a fresh download? And why do they differ? Is there a hacker at loose?

---

### Post by davarino on 2007-12-29
I notice that there was no response to your latest.

There are *no* differences between sites regarding the md5sums.

The difference could have been caused by several things... but the long and short of it all is: you should re-download. :( I would suggest BitTorrent downloading if it is available to you, because it will check the blocks as they come to you. It may be slower, but it's better... especially on a noisy connexion.

If you are interested in several possible causes:

[LIST]A bad connexion during your download. (Often happens.)[/LIST]

[LIST]A change in the standard file between the time that you downloaded and the time that you obtained the checksum. There will be occasional updates: some to fix buggy ISO files, for example.[/LIST]

[LIST]Your suggestion of a hacker is unlikely. It *has* happened (to Ubuntu, no less!), but it's not something that you have to clutter your mind with.
[/LIST]

Best wishes.

---

