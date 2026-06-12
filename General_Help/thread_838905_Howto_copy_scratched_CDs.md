---
title: "Howto copy scratched CDs?"
date: 2008-06-23
forum: General Help
---

### Post by dxxvi on 2008-06-23
I have some scratched unprotected music cds. Anyway to copy those cds to new cds so that a cd player can skip bad tracks in the new cds?

---

### Post by mempman on 2008-06-23
get some cd cleaner...no OS can help u recover data from a scratched cd....:(

---

### Post by Taxman415a on 2008-06-23
Well sure, if you just do it manually and create the new cd without the bad tracks you'll have that. But you should be able to recover the songs either by using Grip (install if from Add/Remove or Synaptic etc) which uses cd paranoia to aggressively error correct to try to read damaged cds, or by physically polishing the cd itself. Brasso works well as it is a very fine abrasive. Put some on a soft cotton cloth and rub away. You can actually use a slightly more aggressive abrasive if you don't want to put quite so much elbow grease into it, but be careful on the polishing/rubbing compound you buy--if it's too aggressive it will scratch the disk or wear through it too fast. What I do is put some compound on a cloth polishing wheel, mount it on a drill and carefully buff the disk. I've not yet had a scratch I couldn't take out enough to make the disk readable, but if the scratch hits the data layer, you're done for. I also took a piece of a flat board and use a bolt and a wing nut and washer to secure the cd to it to keep it flat, keep it from bending while I polish it, and so it's easier to hold on to. If you bend the cd too much you'll ruin it that way too.

---

### Post by cariboo on 2008-06-23
You could try making a duplicate of your CD using the dd command eg:

```
dd if=/dev/cdrom of=cd.iso
```

the /dev/cdrom should be the device that is listed in /etc/fstab as your cdrom drive eg: /dev/scd) in my case.

What this does is create an image of you cd and formats it as an iso you can then open your favorite cd burning software, usually the choice to burn an image is located in the Tools menu.

Jim

---

### Post by molotov00 on 2008-06-23
two things:

pc cdrom drives are more sensitive than music player cd drives. so to copy them you'll need to error correct a taxman is saying

i'd simply polish them up. i've always used toothpaste -- music cds, data cds, ps2, even xbox360 games have been completely fixed by applying toothpaste with my finger on the cd. when a cd scratches it's just the plastic (unless you've got the shiny data layer peeling and that's no good). so what you're doing is grinding down the plastic so that the laser isn't deflected and thrown off, as is the case when there's a big scratch. many little scratches (i.e. toothpaste) is better than a single big scratch if you're trying to read a disc.

Jim: you posted JUST before me but I didn't know you could do that. Cool.

---

### Post by |{urse on 2008-06-23
I generally just stick my old unusable cd/dvd's in the microwave for 4 seconds. Lol, what fun. (don't do it until you've gotten the data off of course.

---

### Post by LoneWolfJack on 2008-06-23
In fact, one of the best and cheapest polish for CDs is... toothpaste.

Not kidding... yields awesome results for slight scratches.

---

### Post by ramjet_1953 on 2008-06-24
I have had good success by putting some very fine grit car polish on a lambswool buffer and giving them a polish.

They usually come up like new. Don't be too agressive, though!

Grip will also probably recover them, but be prepared to let it run for a very long time, if the CD's are badly scratched.

dvddisaster can also be used to provide 'insurance' for your undamaged CD's and DVD's if they become damaged in the future.

Regards,
Roger :cool:

---

### Post by darbid on 2008-06-24
I too have used toothpast on the scratches - it should get you by just long enough to get a copy.

---

### Post by Yondergod22 on 2008-06-24
you could download the songs from mininova.com or limewire or something, im pretty sure its not illegal if you own the CD

---

### Post by logos34 on 2008-06-24
> **cariboo907 said:**
> You could try making a duplicate of your CD using the dd command eg:

```
dd if=/dev/cdrom of=cd.iso
```the /dev/cdrom should be the device that is listed in /etc/fstab as your cdrom drive eg: /dev/scd) in my case.

What this does is create an image of you cd and formats it as an iso you can then open your favorite cd burning software, usually the choice to burn an image is located in the Tools menu.

Is that all you need to do?  never thought of that

but if the cd is badly scratched, how can dd read succeed where a ripper fails?

---

### Post by mc4man on 2008-06-24
I would try grip, if not there are some win. apps that might work. Eac is pretty good at error correction, works great in gutsy, hardy is troublesome. Blindwrite (blindread) used to work very well also, who knows since Vso took over. Does work fine in wine,(just tried), free 21 day trial.
dd will abort when finding unreadable sectors, this works but will possibly butcher any tracks with unreadable areas and may take quite some time.
dd if=/dev/scd0 of=cd.iso conv=noerror,sync

---

### Post by smatiauda on 2010-01-11
Try cdparanoia

---

### Post by Roy Samuel on 2011-06-09
Use ddrescue to copy a disc to an iso image. The 'noerror' option provided in the command below, tells ddrescue to continue inspite of input read errors. The 'sync' option fills the output image with nulls at the point where the CD/DVD is scratched or unreadable. 

ddrescue if=/dev/sr0 of=/home/roy/rescued_cd.iso bs=2048 conv=notrunc,noerror,sync

Mount the iso file using a loopback with the command below:

mount -t iso9660 /home/roy/rescued_cd.iso /mnt -o loop

This will mount your recovered CD image to /mnt partition where you can access it using Nautilus.

---

