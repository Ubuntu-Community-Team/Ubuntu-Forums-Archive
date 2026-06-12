---
title: "Honestly how do i install this.?"
date: 2006-07-04
forum: General Help
---

### Post by Cokemonkey on 2006-07-04
Okay, i searched the forums already.. too confusing.. im planning on putting ubuntu on the computer im making for my sister, but all i see is a boot cd download, how do i actually make this hero OS?

---

### Post by aysiu on 2006-07-04
Read these two links.
[http://www.psychocats.net/ubuntu/iso.html](http://www.psychocats.net/ubuntu/iso.html)
[http://www.psychocats.net/ubuntu/installing.html](http://www.psychocats.net/ubuntu/installing.html)

---

### Post by Cokemonkey on 2006-07-05
Thanks much.... after using both KNOPPIX and Feather Linux, i assumed ISO meant it was live only. thanks bud.

---

### Post by Cokemonkey on 2006-07-05
This is starting to get annoying, i installed the iso file to a disc, (burned image with nero, 8x optical speed) doest work. forces me to restart. so i remove the disc, and i (attempt to) md5sum it. i rightclick the md5 file and click check sums. it comes up with this:

[img]http://img109.imageshack.us/img109/9633/untitled9kz.png[/img]

okay so no big deal, the disc didnt work. so i go back and i rdl the same iso file. i do an md5sum, on this new one. and it say the same thing! is it normal to have 2 problems in a row, or am i doing something wrong? i had no problems with knoppix or feather linux.. sorry if im being annoying, but im a beginer with this..

---

### Post by cowley on 2006-07-05
hi, the iso has to be burned as a cd image, and the slower you burn the better.  i burn it as 4x on sony disks and i have never had a problem

then set your bios to boot from cd and run the livecd - when ubuntu boots from the cd on the desktop is an install icon - and away you go!

simon

---

### Post by nalmeth on 2006-07-05
It looks like he did burn as an iso
At a decently low speed too.

What exactly went wrong during boot up?

Where are you downloading this image from? Maybe try a torrent download instead.

---

### Post by playmobiel on 2006-07-05
maybe he burned to iso to a cd , like data, so the iso file is on the cd, but he didn't burn it as an image

---

### Post by cowley on 2006-07-05
[QUOTE=playmobiel]maybe he burned to iso to a cd , like data, so the iso file is on the cd, but he didn't burn it as an image[/QUOTE]


thats what i think

simon

---

### Post by Cokemonkey on 2006-07-05
No.. **i burned as an image**.. at as slow as my buring program could go. (8x) i used the regular file from the very first mirror on this list. this time i dl ill use torrent dl.. [running the live cd] when i ran the file in the begingin it worked but when i click run of install (the first thing on the list) it loads for a second from the cd.. and then it comes up with an error and forces me to reboot.

---

### Post by Cokemonkey on 2006-07-05
This is getting really gay. i dled as torrent file and redled the md5 sums and it stil doesnt work. same md5 problem... is there something wrong with md5summer or am i just an idiot?

---

### Post by jocko on 2006-07-05
Do you get any error message when the boot fails?

---

### Post by Cokemonkey on 2006-07-05
yea. thas what i mean by force restart.

---

### Post by 11hjpphty76lkjj on 2006-07-05
What is the EXACT error you got on trying to boot from the livecd? 

I've done this more times than I can count with no problems..

---

### Post by Cokemonkey on 2006-07-05
oh sorry. i misunderstood the question. brb.

---

### Post by Cokemonkey on 2006-07-05
"error reading the boot cd"

when u click run or install or watever it says..

---

### Post by nowadays who knows on 2006-07-05
Another question is are you doing the md5 sum from the desktop on the files or on the cd after burning it? If it is from the desktop then you are definatley having issues with what has been downloaded and not the burn process. If this is case with the md5 from desktop try torrent download or a different mirror.

---

### Post by Cokemonkey on 2006-07-05
i torrent dled the file, opened the corect md5 sum text document, saved as samething + a .md5 at the end, and double clicked the md5. it comes up that problem. =)

---

### Post by Cokemonkey on 2006-07-05
Ah ha!

ok this time i right clicked the iso file i dled and i got sums for it, then i checked the md5 sum i dled as a text file manually, and NOW they match. it was jsut a problem with the md5summer (I THINK)

---

### Post by s_h_a_d_o_w_s on 2006-07-05
Download the image (get the live CD, once it boots up, on the desktop, select the ''Install'' icon). Once you downloaded it (say to your desktop) right-click it and select: 'burn to cd'. Then reboot, press ''esc'' when it starts up, to enter your BIOs. In there, select the cd-rom as primary boot device. Save and exit settings. Voila!, it should boot up in the liveCD, then do what I wrote in parentheses up there. Good luck.

---

### Post by devnulljp on 2006-07-05
If you look at that windows error, it's using DOS 8 character names, so it's not surpirsing it can't find the ISO.
Try moving the iso to C:\
change its name to something like ubuntu.iso
try to burn the iso

Make sure your PC can boot from the CD/DVD (in the BIOS - make sure CD/DVD comes before HDD)

Boot from the disc.

---

### Post by Cokemonkey on 2006-07-05
nope it was just a problem with md5summer, cuz im running ubuntu live right now. thanks for the help everyone i got it now.

---

### Post by jimmygoon on 2006-07-05
You are not using the md5summer properly. Its looking for the ISO in a different place... because it says "not found" rather than "bad md5" or something else...

How about some more feedback as to where it reboots/halts and/or what it says at that time? (Also do you notice anything during the boot up of the live disc)

OH OH! Try the alternate installer!

---

### Post by Zyphrexi on 2006-07-05
I always had a hell of a time with burning cds for some reason myself. Wasted over 12 probably.

---

### Post by Cokemonkey on 2006-07-05
Well.. ive wasted 2. and only 1 was with ubuntu. but it wudda been more if i didnt have any help. anyways im not monitering this thread anymore nwo that ive figured it out. thanks much to all of you.

---

