---
title: "enlarge the ubuntu partition"
date: 2008-02-24
forum: General Help
---

### Post by kboy on 2008-02-24
hi, i have  9.80 GB of unallocated space, is there a way to add this space to the ubuntu partition?
without losing the data!!!
i tired to look in the documentation of gparted but i couldn't find anyway to it!

---

### Post by rapiscan on 2008-02-24
If the free space and your current partitions are contiguous, you should be able to use gparted to resize your partition.  Launch gparted:
```
sudo gparted
```
You will be presented with a graphical interface that will allow you to resize your partition.  The "free" partition must be unformatted.

---

### Post by kboy on 2008-02-24
thank's for the reply!
how do i know if the partitions are contigous, you see, the 9.80 GB of free space is from the partition of windows xp.

---

### Post by rapiscan on 2008-02-24
Ok, this is quite a bit more complicated then.  In referring to "free" space, I was referring to unpartitioned space.  Since you would like to use free space on your windows xp partition, you would first have to shrink the window xp partition so that you have created a new unpartitioned space.  

However, it's really unlikely that both your ubuntu partition and your xp partition are sitting right next to each other, so this wouldn't work out for you.

Honestly, if it's at all possible, I would recommend purchasing a new harddrive (or finding an old one lying around) instead of trying to resize in this way.

---

### Post by .nedberg on 2008-02-24
You can resize and move partitions with gparted or qtparted. They are on the LiveCD of Ubuntu and Kubuntu. Use the LiveCD to do this. What you want is doable, and not very hard.

But remember that there is always a possibility of loosing data this way! So backup first!

---

### Post by rapiscan on 2008-02-24
.nedberg,

It's unlikely that the two partitions are contiguous, in which case kboy won't be able to do this.

---

### Post by .nedberg on 2008-02-24
They don't need to be continuous as he can move them.

I did this myself once and it is indeed doable.

---

### Post by rapiscan on 2008-02-24
Thanks for the info nedberg, I didn't realize gparted allowed you to move the partitions around in this way.  Sorry for the misinformation kboy, looks like it is possible.

---

### Post by banelos on 2008-02-24
Yeah if he has the XP partition first and then the linux, it should be possible to shrink the XP partition, move up the linux one and then add the unallocated space to the linux partition.
I personally have had bad experiences with shrinking windows partitions so I probably wouldn't do this.

---

### Post by .nedberg on 2008-02-24
No problem rapiscan!

I would also recommend against doing this if it is only 9.8GB.

But if you want to take the chance remember to backup everything!

---

### Post by Ian222 on 2008-02-24
I have a similar concern. My Windows XP partition is first followed by my Ubuntu partition. I'd like to expand the Ubuntu portion. When I ran qtparted I got the following error:

X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 158
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed

I then tried unmounting the windows partition. The option to re-size the partition was gray, so I couldn't do anything. I tried using gparted and it said it couldn't read the contents of the filesystem after I unmounted it, so some operations may be unavailable. 

I have already run a disk check and de-fragmented the windows partition. I would appreciate any suggestions. Thanks in advance.

---

### Post by geo909 on 2008-02-24
gparted seems to work fine for such situations.
Many people have used it succesfully.

But I would give a +1 to the backup advice. Don't skip that!

---

### Post by imoatama on 2008-02-24
I just did exactly this - reduced my XP partition by 10gb and increased my ubuntu partition.
I recommend you download and burn the Gparted livecd. Boot into that, and shrink your XP partition - best to have defragged etc first so the free space is all in one big block (ie contiguous) at the end of the partition.

Once you've done that you can grow your ubuntu partition, Note that this can take a long time, because if you're adding space to the start of the partition (which it sounds as though you're doing) then it will need to move the entire file system 'to the left' so it starts at the beginning of the partition. This took 2+ hours for me on a new laptop, and only 4GB to move!

Good luck!

---

### Post by kboy on 2008-02-24
man....... i've already tried everything!!! nothing works (actually i don't work).
i've tried Gparted, patred magic liveCD, and about 10 different guides on how to combine to partitions.....

[ATTACH]60686[/ATTACH]
i've attached a snapshot of the partitions from Gparted.
what i want is to combine the empty sda3 with the ubuntu partition sta8.
i hope someone here will help me.

---

### Post by imoatama on 2008-02-24
It's easy.

1. Boot the Gparted livecd or the ubuntu livecd and run Gparted.
2. Right click on sda3
3. Click 'delete'
4. Right click on sda8
5. Click Resize/Move

You can probably then take it from there.

---

