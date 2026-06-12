---
title: "ok this has been a headache. any help EXTREMELY appreciated"
date: 2007-05-30
forum: General Help
---

### Post by norebonomis on 2007-05-30
I'm not 'l33t' but I'm not a newb. I'm a hobbyist. but i hate windows..
messing around with dual booting this past weeked i messed up pretty bad, and am looking for help on two things;

i had successfully installed both vista business and ubuntu w/ grub bootloader. for some idiot reason i decided i wanted to try reinstalling ubuntu. and deleted the ubuntu partition from vista. from that point on i could not boot either into ubuntu or vista, not only that but even after re partitioning the ENTIRE hard drive. windows xp or vista will not install. this doesn't make sense to me, since i formatted it with the windows installers. ok so back into using ubuntu. and OH VISTA MADE MY SECOND HARD DRIVE a DYNAMIC DISK! (which i assume is why i cant see it in ubuntu now... 

so #1) is there anyway (besides using xp repair and fixmbr because that didn't work) to get windows to reinstall on clean hard disk?
and #2) if #1 is not possible and i am stuck with ubuntu (not a bad thing) can i get ubuntu to read my 2nd hard drive like it was before vista made it dynamic?

---

### Post by Scunizi on 2007-05-30
If you want to attempt a full reinstall of both systems, a downloaded live cd copy of GParted is invaluable.  Boot to that, blow away all partitions, recreate the partitions you want and start fresh.  Let windows format its side and Ubuntu "his/hers".

---

### Post by norebonomis on 2007-05-30
> **Scunizi said:**
> If you want to attempt a full reinstall of both systems, a downloaded live cd copy of GParted is invaluable.  Boot to that, blow away all partitions, recreate the partitions you want and start fresh.  Let windows format its side and Ubuntu "his/hers".

i can tell this is going to be a project, going to have to figure out out to burn a live cd inside ubuntu because it's all i have right now. thanks for the tip

my second question still stands, is there anyway for ubuntu to read my second hard drive(dynamic, whaver that means) so i can backup data over my network?

---

### Post by Neobuntu on 2007-05-30
1st, everyone be careful with manual GRUB. Never (generally) do any command in GRUB and with setup accept...```
setup (hd0)
```
Maybe setup (hd1) if booting from a second drive. Don't write the GRUB stage 1 over your installed OS partition (you'll likely have to reinstall). It goes in the MBR (which is like a partition of it's own at the start of your drive); thus only one numeral. Please petition GRUB to add a warning string. Let the easy; fast, live, installers do your GRUB for you (safely).

Anyway, If you have already started over from scratch, boot a live CD and use the partitioner to delete everything (MBR, partitions) and write them over anew.  Then you might erase them again so the OS installer may decide all . Then install Windows first (or just don't use windows, it wastes your time). Can you get by with WINE or Vmware, Virtualbox or Zen? Do you need to just need to find a native open replacement (like Kmymoney for Quicken)? Still, run a simple dual boot (with your old paid for Windows) and have both as simply native for comparison (if you have time for Windows).

Vista users must bone up on Microsoft's latest land mines (first). Personally, I already know Vista stinks.

"Give me liberty or give me death"

---

### Post by norebonomis on 2007-05-30
> **Neobuntu said:**
> 1st, everyone be careful with manual GRUB. Never (generally) do any command in GRUB and with setup accept...```
setup (hd0)
```
Maybe setup (hd1) if booting from a second drive. Don't write the GRUB stage 1 over your installed OS partition (you'll likely have to reinstall). It goes in the MBR (which is like a partition of it's own at the start of your drive); thus only one numeral. Please petition GRUB to add a warning string. Let the easy; fast, live, installers do your GRUB for you (safely).

Anyway, If you have already started over from scratch, boot a live CD and use the partitioner to delete everything (MBR, partitions) and write them over anew.  Then you might erase them again so the OS installer may decide all . Then install Windows first (or just don't use windows, it wastes your time). Can you get by with WINE or Vmware, Virtualbox or Zen? Do you need to just need to find a native open replacement (like Kmymoney for Quicken)? Still, run a simple dual boot (with your old paid for Windows) and have both as simply native for comparison (if you have time for Windows).

Vista users must bone up on Microsoft's latest land mines (first). Personally, I already know Vista stinks.

so i'm pretty much stuck with some variation of linux as my primary OS? that doesn't make sense, maybe i'm reading your post wrong. god if macs weren't so expensive!

i guess will try having ubuntu as primary and dual boot into vista, but WHY OH WHY is it impossible to go back to just windows.

i used an XP disk's fixmbr, but windows stills says it's not a valid partition or whatever

and also anyone know anything about acessing my second hard drive that vista made dynamic?

---

### Post by Neobuntu on 2007-05-30
I didn't say that.

I meant that Windows wastes more time than open solutions IMHO. But that's another subject.

I was only explaining that sometimes (if you already started over and that horse has left the barn) you might need to rewrite the MBR and partitions, then erase them (I'd recommend) and let the new open installers set it up correctly by default, if there's no great reason otherwise.

It is my advice, to lay a good and long lasting foundation. Thus dual booting (with Windows first) is your first decision. I was just attempting to make it easy for you. Either you want to keep up two OS's or you don't. Obviously, a newbie can tread lightly by adding Kubuntu (for example) after Windows. 

Experienced users know that having Windows around can have more disadvantages than just Kubuntu (and that's my opinion). 

It's all about choice and consequences. Choose wisely (and doing both is fine). You get the best of both worlds (AND the worst as well). It's about your time, your freedom and your future..

That's just the way it is.

---

### Post by Neobuntu on 2007-05-30
Perhaps your GRUB stage 2 (the menu) is just gone; along with Ubuntu and it's partition. If I were you I would look up the manual GRUB commands to  start your Windows partition (from a live CD with GRUB). Just press c at the GRUB live menu. Type help.  Usually...
> title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

(title and savedefault optional) and if any special needs are required for Vista. If this works, it's just a matter of reinstalling just Ubuntu (as you were doing) and then fixing the GRUB entry for Vista (if not automatic). 

If this does not work you may have accidentally written over your Vista partition (the GRUB setup misuse) and if that is not backed up (and there is a way to back-up what GRUB misuse may have trashed but if one knows this, one probably wouldn't misuse GRUB.), then you will have to reinstall what is not there. Reinstalling being the likely best and shortest (but long and painful) course of action.

---

### Post by Scunizi on 2007-05-30
Back to your question about the other drive.. It sounds strange that Vista would make the secondary drive a virtual drive.  To me (and I may be wrong) that implies swap space or a RAID configuration.  The other option I can think of is it tied both drives together to act as one large storage space.  You may be able to mount it with the live cd to see if you can see anything on it.  I'm running Dapper so my fstab might look different that what is presented on edgy or fiesty but I'll give you a couple of lines to try and mount it.  

First get to the terminal at Applications / Accessories / Terminal
Now type fdisk -l ... the letter after the "-" is a lower case L.
This will give you a list of all the drives in your machine and the partitions.

If you have ide drives they should be labeled hda, hdb. A is primary and B is secondary.  Partitions are labled hda1, hda2, hdb1, hdb2 etc.......
So your secondary drive will be hdb1,2,3 etc..it will show how many partitions you actually have on that drive.  Probably one by the sound of it.  It will also tell you the file system type.
NTFS, Fat32, Vfat, etc.

If it's hdb1 you'll need to create a directory for the files to show up.
In the terminal type "sudo mkdir /media/hdb1" (without the quotes) <enter password & enter>
Now type "mount /dev/hdb1   /media/hdb1     ntfs   defaults,nls=utf8,umask=007,gid=46
0     1" and hit enter. If it doesn't give you an error you can now type "cd /media/hdb1" enter and you should be in the drive.. Type ls to get a directory listing. That's LS lower case.  If you see a bunch of files you'll be able to copy them off someplace.

You may also be able to mount the drive by just typing "mount -a, 

If your drives are large and you plan on installing a dual boot system again, what I have done in the past is disconnect the secondary drive as it is.  Delete the partitions on the primary drive with Gparted.  Install Windows first, then install ubuntu.  After all is completed and running, shutdown and plug in the secondary drive and see if windows recoginzes it.

I hope this help.!

---

### Post by wpeteroy on 2007-05-31
Okay well I'm not sure if you nuked your box yet or not but to recover vista and then start again ...

start at step IV here - [http://5363.blogspot.com/2007/05/adding-feisty-to-your-vista-fast-and.html](http://5363.blogspot.com/2007/05/adding-feisty-to-your-vista-fast-and.html)

and then go back to step II.

I'm pretty sure that'll fix you up...

---

