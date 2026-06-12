---
title: "Help making ISO file from cd"
date: 2008-05-06
forum: General Help
---

### Post by drunkmatador on 2008-05-06
Hello, I'm trying to make an ISO file from a playstation game that I have in the cd drive right now, and am running into some problems. 

When running dd if=/dev/scd0 of=re2.iso I get:

dd: reading `/dev/scd0': Input/output error
32+0 records in
32+0 records out
16384 bytes (16 kB) copied, 0.858719 s, 19.1 kB/s


It doesn't make the ISO at all. I'm not sure why. Tried it with the drive mounted and unmounted both with no luck. Does it have something to do with my drive being called scd0 instead of cd0? I think that just means it's SCSI but I am not positive.

Maybe is there just a GTK tool I can download that will help? Earlier I went to windows and used Magic ISO to make one but I hate having to do that.

---

### Post by logos34 on 2008-05-07
There's ISO Master.

Since I upgraded I noticed Hardy wrote '/dev/scd0' to fstab whereas previously it was '/dev/hdc'.  Odd thing is hardware detect and the system still sees the drive as hdc.

sudo lshw -C disk

So try '/dev/cdrom' or /dev/hd[a-d] depending on which ide channel it's on

---

### Post by MaindotC on 2008-05-07
Soda Popinsky LOL!!  Dude, can't you just insert the CD and right-click it to "Open with CD/DVD Creator" ?

---

### Post by drunkmatador on 2008-05-07
Does CD/DVD Creator make ISO files from a CD, and not just burn them?

Ha yeah, he was always my favorite. I think he was the last one I'd beat until Bald Bull cloberred me, too. :)

---

### Post by MaindotC on 2008-05-07
> **drunkmatador said:**
> Does CD/DVD Creator make ISO files from a CD, and not just burn them?

Nah you can select "File Image" and place it/name it wherever/whatever you want.  I attached a pic so you know what you should see.

Do you play NES or SNES emulators?  I can't get enough of Super Punch Out on ZSNES :)

---

### Post by drunkmatador on 2008-05-07
Well when I try to open the drive in CD/DVD Creator it gives me this message:

The file '/home/mozzles/.gvfs/cdda mount on scd0' is not a valid disc image.

This drive I'm using has some problems.. it's slow and will stop spinning sometimes, but I can always manage to install OS from it and play psx games and so on.. just maybe it's adding some quirks to ubuntu for some reason. Any ideas?

Yeah I play emulators all the time. Been playing Earthbound with my girl the past couple weeks, it's an old favorite. Love the RPG games the most but super nintendo was great all around.

---

### Post by MaindotC on 2008-05-07
A girl who has an interest in playing games with you - I really need to find these women!

I'm doing some site searches of ubuntuforums via google and I haven't found much - a lot of people having the same problem but no solution seems to be present.  Is it possible to swap out the cd drive and try it on that?

---

### Post by drunkmatador on 2008-05-08
Eh well.. I just decided to put the cd into my desktop, which has a working cd-rom, and rip the ISO on there. Just put it onto a pen drive and I'm about to get off my *** and go grab it so I can put it on this laptop. =)

Yeah she's great, but honestly I'm more stoked about her knowing how to play instruments. It's a lot of fun to play music with whomever you're dating.:-({|=

---

### Post by MaindotC on 2008-05-08
Any chance there could be a problem w/ the cd-rom drive?

---

### Post by philgenius on 2008-10-18
On the desktop, right-click on the CD icon and click "Copy CD". Then write as an image file.

---

### Post by Bucky Ball on 2008-10-18
Brasero? That makes all my iso's without a hitch.

---

