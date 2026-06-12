---
title: "Resize Vista partition using ubuntu's installer?"
date: 2008-02-15
forum: General Help
---

### Post by rollinroll on 2008-02-15
Hi i already have Vista installed and would like to dual-boot with ubuntu.
The problem is, vista's partitioner won't let me resize  it more than 2 gigs i have tried everything like defragmenting etc with no luck.
So i was wondering, is it safe to resize a vista partition using ubuntu's live cd installer?

---

### Post by jan quark on 2008-02-15
make a backup of you important data now

if you want to play with partitioning

and I do not know if it is safe
the gparted partitioner is perhaps to straight forward and will really do what you tell it to do
but wait for others who have done such a thing

---

### Post by rollinroll on 2008-02-15
Thanks for your reply.
I might try Gparted live cd but i will wait and see if some other people replies and confirms that it works.

---

### Post by kesman on 2008-02-15
I think the partition you are trying to resize is formatted as ntfs right? I've never had problems resizing windows partitions, but it seems quite weird that Vista's partitioner wont let you do that. There's gparted in ubuntu install cd, so you won't be needing gparted livecd for that. Is there enough free space on the partition you are attempting to resize? I'm just guessing reasons why Vista wouldn't let you resize the partition, but perhaps there is no reason, since it's a windows program :P

---

### Post by rollinroll on 2008-02-15
> **kesman said:**
> I think the partition you are trying to resize is formatted as ntfs right? I've never had problems resizing windows partitions, but it seems quite weird that Vista's partitioner wont let you do that. There's gparted in ubuntu install cd, so you won't be needing gparted livecd for that. Is there enough free space on the partition you are attempting to resize? I'm just guessing reasons why Vista wouldn't let you resize the partition, but perhaps there is no reason, since it's a windows program :P
Yea, it's ntfs. I think it's weird that vista can't resize it too as i have 211GB free space :mad:
I know ubuntu's partitioner can resize XP partitions but it may not be compatible with vista partitions and that is why i am asking.

---

### Post by kesman on 2008-02-15
It doesn't matter what OS's partition you are trying to modify, was it XP or Vista doesn't matter.

I'd say it's safe to resize the partition, and if you have defragged it, it's even quite fast. Boot to your ubuntu livecd and see what the partition manager has to say about resizing it.

---

### Post by rollinroll on 2008-02-15
Thank you very much for your reply.
Ok, i will try what you said and report back if i have any problems :)

---

### Post by kesman on 2008-02-15
You do that.
You can browse internet from the livecd itself, so report back if gparted gives you any errors.

---

### Post by rollinroll on 2008-02-15
Ok, i am in the live cd now ready for install.
But i have a question, on the resizer thing when it says New partition size: blabla GB does it mean the new size of the windows partition or the new size of the ubuntu partition_

---

### Post by rollinroll on 2008-02-15
Hmm... this is really weird. When i have choosed how much Gb's to resize and click forward the resize option just dissapears and remains with the "use entire disk" and "manual" option. This is very weird.

---

### Post by rollinroll on 2008-02-15
And now, when i restarted the installation program only two options are available: "Use entire Disk" and "Manual"...

---

### Post by rollinroll on 2008-02-15
Sorry for quad posting but when i try to resize it with Gparted it can't resize it the resize option is greyed out and there is a lock icon on the partition wich means its... locked i think.

---

### Post by kesman on 2008-02-15
I have no idea what the lock means in the partition... Maybe you should try the gparted livecd, or some other partitioning software. Perhaps there's some free software for windows too that you could use? :P

---

### Post by ajgreeny on 2008-02-15
Sorry to butt in at this late stage, but I have heard of people having problems with vista after it has been shrunk with gparted, and I thought the general advice was to use the vista partitioning software rather than gparted.  Why it won't work for you, I cant imagine.  As to the option in gparted being greyed out it is probably because the partition is mounted, so unmount it and try again ```
sudo umount /dev/*d*#
```However, be warned about my gparted comments and make sure you are backed up first.

For more info have a look at:-
[http://liquidat.wordpress.com/2007/04/18/shrink-and-move-windows-vista-partitions/](http://liquidat.wordpress.com/2007/04/18/shrink-and-move-windows-vista-partitions/)
[http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/](http://vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista/)
[http://ubuntuforums.org/showthread.php?t=630079](http://ubuntuforums.org/showthread.php?t=630079)
which give information and some warnings about all this.

---

### Post by rollinroll on 2008-02-15
Thanks for your reply.
So i can unmount it wth gparted first and then try ubuntu's installer to shrink the partition? I already tried a 3rd party app for windows but of course it didn't work it said "Invalid partition size blablabla."

---

### Post by kesman on 2008-02-15
You can unmount it in the livecd, either with the terminal command or somewhere in the graphical user interface. I'm on a windows pc right now so I cannot remember the exact location to unmounting the partition, but it's there.

---

