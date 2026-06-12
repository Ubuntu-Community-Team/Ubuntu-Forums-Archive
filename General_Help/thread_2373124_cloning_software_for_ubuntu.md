---
title: "cloning software for ubuntu"
date: 2017-10-03
forum: General Help
---

### Post by pyrforos on 2017-10-03
hi community

So  i  have the following problem: I  have 2 hdd drives 1TB  each.One of them is failing ,and the other one  is old and slow , so i  bought another one of 3 TB to replace them both. I'm  a computer technician and im obligated to use  win 7  win 8  and win 10 for specific programs (vm is not an option ...)and  my  main Os is Kubuntu 17.04. So 4 OSs in  total : win 8  and win 10  in  one drive  , and kubuntu  and win 7  in the other ....
 What  i  want to  do , is transfer all my OSs and my  files fron  the old drivers to  the new big one . Is there a way  to  do  this?
Thanks everyone

---

### Post by gordintoronto on 2017-10-03
The normal way to do this with Linux is rsync. I have read that there is a Windows version. (I only use rsync to back up my home; if my drive fails, I will do a clean install and recover the data.)

Setting up grub might be a challenge. Also, SDA/SDB issues.

---

### Post by Bucky Ball on 2017-10-04
You might find [Clonezilla]("http://clonezilla.org/") useful. fsarchiver or partimage are other possibilities. Have [a read of the links on the fsarchiver site]("http://www.fsarchiver.org/cloning-ntfs/").

As mentioned by gordintoronto, you will no doubt have some issue or the other with grub and booting once transferred, but that is fixable. I swapped my Win and Xubuntu installs from HDD to SSD a couple of years ago (I think using Clonezilla) and few probs, not long to fix, though. Boot Repair is probably your friend then.

I suggest you prepare yourself with bootable Ubuntu install media (or Boot Repair) so you can boot to a 'live' desktop anytime you need to. Both of those have Gparted so you can easily see what's gone where and create new partitions for your clones if and when you need to.

(PS: The [stable version of Clonezilla]("http://clonezilla.org/downloads/download.php?branch=stable") is the one to use if you go that way. Good luck.)

---

### Post by pyrforos on 2017-10-05
thanks guys!:)
I think  clonezilla is what i  want... Im  thinking to  even resize all partitions and even to clean up all my scattered files in 2 more partitions... If i  use the  option "clone partition to partition" , for the OSs and then use  from a live usb a boot repair tool you  think ill  be ok or i  have to  do  a fixboot for every win partition  ?

---

### Post by Bucky Ball on 2017-10-05
> **pyrforos said:**
> If i  use the  option "clone partition to partition" , for the OSs and then use  from a live usb a boot repair tool you  think ill  be ok or i  have to  do  a fixboot for every win partition  ?

That should work, yes. Defragment any Windows partitions several times before cloning.

Thing is, there may still be confusion with boot as your SSD will probably be sdb, not sda. Your HDD is currently sda? If so, it will stay that way and the system will be cloned to the sdb drive. Are you using UEFI boot or legacy? This is also a consideration. 

Some machines will insist on booting from the first hard drive, sda, and so it is sometimes easier to just swap the drives. I did this with my laptop and it helped to fix things. Once the clone is complete, you might want to take the HDD out for the moment, put the SSD where it was, boot and see what happens.

If a fail, resort to Boot Repair, check the SSD is sda (you can do this with Gparted if you create bootable Boot repair media). If so, use BRepair to specify sda as the location to install grub.

---

### Post by pyrforos on 2017-10-06
absolute failure.... i m struggling here for the past  6 hours and i cannot  make it work...
I cloned all  my OS's partitions and then i  used Boot Repair as  Bucky Ball said. I can log in to  Kubuntu  but at  the grub  menu there is only windows 10 and when i  select it there is only a back  screen with a dash  blinking...I  tried to modify  /etc/grub.d/40_custom but with the same results... maybe im  too tired to think... i dont know 
please help

---

### Post by efflandt on 2017-10-07
Are you using legacy BIOS or UEFI? If your old drives used **msdos** partitions, you CANNOT clone those to a 3 GB drive because msdos partitions are limited to 2 GB maximum drive size and the 3 GB drive would need to use **gpt** partitions.

Another problem is that the partitions all on one drive with different partition numbers would confuse whichever Windows is likely booting the other 2 Windows based on drive and partition they used to be on. When you install multiple versions of Windows, one of them usually handles booting the other Windows versions. That may also be a mess for any Windows programs looking for anything not on their own partition (which is usually C: for which ever one is booting at the time). So you may need to install each Windows, then figure out how to copy (almost) everything over to them except related to booting. Then install Kubuntu.

The only experience I have running multiple Windows versions was when I installed 64-bit WinXP Pro beta along with 32-bit WinXP Home. In that case WinXP Home booted both of them using the 64-bit ntldr (boot loader) copied from the 64-bit system. I later replaced both expired 64-bit WinXP beta and SuSE with both 32-bit and 64-bit Ubuntu 10.04 (which it still has, but rarely used unless I need to grab old files). So I am not sure which file or file format Win7, 8 or 10 would use to boot the other 2 Windows from one of them.

---

### Post by pyrforos on 2017-10-07
hi  again
In fact  efflandt  i  tried to make a clean install of WIN 10 hoping that this will take care the other windows partitions but i got a message saying that my drive is in gpt...(my mobo is a bit old so i use BIOS not UEFI)
>  you CANNOT clone those to a 3 GB drive because msdos partitions are limited to 2 GB maximum drive size and the 3 GB drive would need to use gpt partitions.
I presume you  mean 2 TB no GB.. my partitions are circa 100 GB each... my new drive is 3TB... Is that the problem?Im really  confused here ...
So in your opinion the only thing i can do is to install all my OSs from the beggining? That would be terrifying ..  :o 

im going to  try to clone all the old drives "as is" to the new one to see what happens...  10 hours and counting..

---

### Post by leunam12 on 2017-10-07
You are attempting to do a quad-boot by simply cloning partitions and without re-installing anything, seems like a monumental task. If you can accomplish this please post a step by step procedure as this is very interesting. I would try to have the 3 Windows systems working first and then add Kubuntu.

---

### Post by pyrforos on 2017-10-07
ok i made it! Total  time : 17 h as seen my S.M.A.R.T data :P
How i  did it :
1.Cloned with Clonezilla the whole DISK not partitions , with kubuntu and Win 7
2. pulled out cloned drive left only  the copy.As it has the  boot loader already boots fine (has the other two entries but  just  don't try to  see if they  work they  don't ...) 
3. installed win 8  normally and after that win 10 also normally.Things for all Win OSs are taken care by win 10(i tried and tried but if you  clone them you  end up with a gpt partition error )
4.copied by  live cd  all my files and configuration  files to appropriate folders so when i install them they will  be ready
5.boot  form  live cd  with boot-repair

What i observed is some fails at win 10 booting sequense... but after a restart everything was ok... any  ideas on  that?

---

