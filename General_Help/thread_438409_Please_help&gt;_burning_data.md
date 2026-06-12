---
title: "Please help&gt; burning data"
date: 2007-05-09
forum: General Help
---

### Post by midlandman on 2007-05-09
Hi.
I'm trying to burn a data dvd ( a few AVI files) and I'm not having much luck. All I'm doing is wasting blank dvds.
No matter what program I use, all it does is close the dvd, and doesn't burn anything on it. So I'm left with an empty dvd that's closed.
If I put a blank CD in, a window comes on asking me what I want to do. But when I put a dvd in, a window comes on saying "Cannot mount volume...invalid mount option when attempting to mount the volume".
Can someone help me out with this? All I want to do is burn the AVI files on a DVD so I can install them on another computer.
Thanks.

---

### Post by Turellius on 2007-05-09
My guess is that you have a standard install and are trying to use programs that are in the standard Ubuntu install.  In the menu under System>Administration>Software Sources make sure both Universe and Multiverse are checked.  Then open up a terminal window and type the following commands, You can either install one or both of these programs but either of them should be suitable for what you are looking to do.

```
sudo apt-get install gnomebaker

sudo apt-get install k3b
```

After that they should be available under Applications>Sound & Video.

---

### Post by midlandman on 2007-05-09
Thanks for the info, but I did everything you said, and it still won't work. When I try with k3b, when it click "burn" I get an error-"could not determine size of resulting image file". And it doesn't offer any resolutions at all.
As well, I notice that when I go to "My computer", it shows my file system and floppy drive, but no cd/dvd rom when I have a dvd in. But it shows with just a regular cd.
I tested my drive to see if the problem was with the dvd/cd rom itself, but I played a dvd without a hitch. But for some reason Fiesty doesn't seem to recognize a blank dvd.
Any ideas?

---

### Post by midlandman on 2007-05-09
Bump...so this doesn't fall off the map.

---

### Post by midlandman on 2007-05-10
Anyone?

---

### Post by Butthead on 2007-05-10
Stupid question, but are these truly "blank" CD's?

The reason I ask is because it sounds very similar to a problem I had with CD's that I first burned stuff on under Windows XP.

My solution (fix?) was to use truly virgin blank CD's.

---

### Post by turbojugend_gr on 2007-05-10
Maybe your drive does not recognize that particular type of discs, try another manufacturer maybe? this is more common on laptops..

---

### Post by mdurham on 2007-05-10
Judging by posts in this forum, there are many problems reading & writing CD/DVD's, maybe this is just another one. Maybe you could report it as a bug.
Cheers

---

### Post by eddieb on 2007-05-11
Try inserting the blank disc and then reboot. I am running 64 bit and found the exact same prob. 
Click on Places-Computer and you should see an extra drive.

---

### Post by midlandman on 2007-05-11
OK, the problem isn't with the blanks. The drive reads them with no problem, but only when they have files on them. I've installed MP3s and vids that I had burnt on them, and Ubuntu read them. It's only when they're blank I'm having the problem.
I rebooted with a full disk and the drive was showing, then rebooted with a blank and the "cannot mount" popped up again then the drive disappeared.
Can someone give me the proper code for "fstab"? I tried "grep "dvd" /etc/fstab" and it doesn't work.

---

