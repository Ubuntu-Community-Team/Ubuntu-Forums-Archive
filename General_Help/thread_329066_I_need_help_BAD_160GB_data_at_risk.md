---
title: "I need help BAD 160GB data at risk"
date: 2006-12-31
forum: General Help
---

### Post by band-aid on 2006-12-31
My brother completely killed his windows install but he needs the data on the drive. I have put in my ubuntu live CD and am trying to somehow get a connection to a shared drive on another windows computer. My two options appear to be mounting it as a samba share (the file is at \\alex\SharedDocs and I want to mount it to /media/SharedDocs but I cannot get the command to work. My other option is to somehow share a folder on the drive but because its read only this is going to be difficult. Any suggestions are greatly appriciated.

---

### Post by Sef on 2006-12-31
Check out [Test Disk]("http://www.cgsecurity.org/wiki/TestDisk").

Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

### Post by GrumpyBob on 2007-01-01
Not really a "real Ubuntu response", but could you remove the drive and put it in the functional windows box?

Robert

---

### Post by dasunst3r on 2007-01-01
For data recovery-related items using anything, I would do something like this:
[list=1]
[*]Turn on the computer and boot into Ubuntu (LiveCD or any other means)
[*]Plug in an external hard disk
[*]Once booted, open up a terminal and do the following (DO NOT BLINDLY COPY AND PASTE!!!):
```

dir /dev/hd* #See what hard drives you got.  You will usually get hda, hda1, etc.
sudo mkdir /mnt/tmp #Make a mount point
sudo mount -t ntfs /dev/hd? /mnt/tmp #Mount the drive of type ntfs.  Replace the ? with the partition number.

```
[*]The USB drive should be auto-mounted.  Double-click on that.  Open up a new window and navigate to /mnt/tmp
[*]Drag-n-drop
[*]???
[*]Profit!
[/list]

I find that to be the best way to go (I'm kidding about the last two steps, by the way).  You will receive different suggestions from fellow members.  Choose whatever suits you best. :)  Good luck!

---

### Post by smoker on 2007-01-01
> My brother completely killed his windows install but he needs the data on the drive. 

why don't you do a windows repair with the windows install cd. a repair will not overwrite your data?

---

