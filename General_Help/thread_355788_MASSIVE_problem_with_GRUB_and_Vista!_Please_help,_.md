---
title: "MASSIVE problem with GRUB and Vista! Please help, not the usual problem!"
date: 2007-02-07
forum: General Help
---

### Post by bijanv on 2007-02-07
Okay so I've been reading and trying for almost 2 days now and I'm getting really scared and frustrated.

I installed vista on my laptop and everything was going fine so I decided to dual boot ubuntu as well. I created another partition and it worked fine except then I decided I wanted to run Vista from the grub loader at startup. When I pressed enter on vista, the computer would automatically restart!

Now to fix this problem, I thought I would just format my ubuntu partition and everything would be back to normal (oh how wrong I was). Now that I've done that, I'm left with the Grub loader that now gives an error since ubuntu was removed and then it hangs.

How can I get my vista back!?

I CANNOT reformat my drive as I have alot of files on vista that I NEED. Alot of what I've read says to use FIXMBR or FIXBOOT except it seems that vista does not have these. I need to find a way to rewrite the GRUB loader with Windows Vista loader...

can anyone PLEASE help!! i'm dieing here!

---

### Post by aberry5555 on 2007-02-07
dont panic! :p it is the normal problem, you just have to understand what it's doing is all. when you installed Ubuntu you installed the GRUB over the windows bootloader, so there's nothing to tell your computer where windows is. The GRUB entry is saying windows is on the first hard-drive, which is right, but all the GRUB does to boot windows is to try and start the windows bootloader (which you don't have anymore). 

Now with XP there are tools on the CD that allow you to recreate the boot-loader on the selected hard-drive, so hopefully there should be the same in vista. Boot up the CD and see if you can get in to a recovery program (it will be a button or in a menu somewhere before you install Vista), for instance the XP version was called the "recovery console" so try to find that. Hopefully they still have it on Vista, though because I don't use it myself I don't know. Post back what you find and I'll try and help you from there.

---

### Post by Dylnuge on 2007-02-07
Notice that aberry beat me to the post. There is some recovery console stuff on the XP disks, and that will get you back to your normal Vista configuration, except without Ubuntu.

If you want to use Ubuntu, you don't need to run /fixmbr, and you can just run the commands listed below.

Ok,

The GURB Loader is located in the Ubuntu partition, the MBR (Master Boot Record) just references it, which means you are going to get an error if you delete the Ubuntu partition. So first, you need to boot from the LiveCD and reinstall Ubuntu over the old Ubuntu partitions (you will want to reformat them as well). This will not harm Vista.

Now GRUB should work. If you still can't get into Vista, but can get into Ubuntu, you need to do the following:

1. Open up Ubuntu.
2. Click Applications->Accessories->Terminal (in GNOME)
3. In the terminal, type in the following command
```
sudo nano -w /boot/grub/menu.lst
```
4. In Nano, scroll through the entries until you find the one which starts with something like:
```
Title = "Microsoft Windows Vista"
```
5. Post what is in that section.

Hope I helped

---

### Post by bodhi.zazen on 2007-02-07
Re-install Ubuntu

During the install, re-install grub into the MBR ...

If you can not boot windows, post the contents of /boot/grub/menu.lst and the output of ```
sudo fdisk -l
```And we will help you get up and going ...

---

### Post by bijanv on 2007-02-07
Yes Vista does have a "repair" section however it is of no use. It even has a "Fix startup issues" but it doesn't help at all.

I've used the command line that it has but fixmbr and fixboot are non-existant

I just read somewhere about using bootsect.exe from the Vista DVD which I did use but it didn't help. Maybe I didn't use it properly?


and thank you for your amazingly fast posts! I will install ubuntu again now and see what happens

---

### Post by aberry5555 on 2007-02-07
In the command prompt that you get on the vista boot-up type in the following to restore the vista bootloader: 

```
C:\boot\ Bootsect.exe &#8211;NT60 All
```

Obviously only use C: if this is the drive letter, though I'm sure it is.

This should help :) it is the replacement for window's NTLDR boot menu.

I got the information from this site:

[http://support.microsoft.com/kb/919529/en-us](http://support.microsoft.com/kb/919529/en-us)

**EDIT**

If you are going to install Ubuntu then you must make sure you install the GRUB on the UBUNTU partition, not the windows one, you can manually add Ubuntu into the vista startup menu later, but the way Vista now works you can't install the bootloader on anything other than the first partition.

---

### Post by xpod on 2007-02-07
CALAMITY KIT:) 

1:Ubuntu live cd
2:Super grub bootloader cd
3:Gparted cd
and  of course a 98 bootdisk with fdisk if you dont have XP\Vista cd`s

And i`m sure theres a few others too people that have in their collections.

---

### Post by bijanv on 2007-02-07
> **aberry5555 said:**
> In the command prompt that you get on the vista boot-up type in the following to restore the vista bootloader: 

```
C:\boot\ Bootsect.exe –NT60 All
```

Obviously only use C: if this is the drive letter, though I'm sure it is.

This should help :) it is the replacement for window's NTLDR boot menu.

I got the information from this site:

[http://support.microsoft.com/kb/919529/en-us](http://support.microsoft.com/kb/919529/en-us)

**EDIT**

If you are going to install Ubuntu then you must make sure you install the GRUB on the UBUNTU partition, not the windows one, you can manually add Ubuntu into the vista startup menu later, but the way Vista now works you can't install the bootloader on anything other than the first partition.

yes I tried exactly that command with bootsect but it made no difference. GRUB would still run. I'm currently reinstalling UBUNTU, should be done in a couple of minutes

---

### Post by aberry5555 on 2007-02-07
hmmm... thats weird... still, if worst comes to worst you can always use Ubuntu to copy across all your important files and then reinstall vista. quick question, is vista installed on the first partition?

---

### Post by bijanv on 2007-02-07
yes, vista is installed on the first partition.

I have no problem reinstalling vista as long as I can backup my documents and files. How would I go about doing that though? Can ubuntu access the other partition that windows is on?

---

### Post by jesus5511 on 2007-02-07
Is it just normal files you REALLY need? Because if so, one option would be to just bring the files over from the Windows partition (through Ubuntu) to back them up, then burn them to a disk or something and reinstall vista and put the backuped files on it.

That of course would be a last resort.

Edit: Someone beat me to it.

---

### Post by aberry5555 on 2007-02-07
Im pretty sure vista uses NTFS so yeah it can read it, but not write to it, unless you install an extra package. type in fdisk -l and it will tell you the partitions on your HD, which will be listed as something like /dev/hda2, /dev/hda7 etc... Determine which one is your Vista partition and then figure out where you want to be able to see it (when you want to see a partition in Linux you have to "mount" it in a folder, so find somewhere you want it and create a folder called "windows" or whatever you want to put it in. an easy place for you would probably be the desktop.) Now go to a console in Ubuntu and type in something like this, for example:


```
sudo mount /dev/hda1 /windows 
```

replace the "/dev/hda1" with the relevant hard-drive and the "/windows" with the folder you want to see your hard-drive in.

---

### Post by bijanv on 2007-02-07
thats great thanks alot! the installation is just about done so I'll see if the past recommendations work and if not then I guess I will just do that.

---

### Post by aberry5555 on 2007-02-07
no problem :) see, doesn't microsoft tech support suck in comparison to Ubuntu :p

---

### Post by Dylnuge on 2007-02-07
Yes, it can. Open up a terminal and type in the following commands:
```
sudo su -
mkdir /media/hda1
mount /dev/hda1 /media/hda1
cd /media/hda1 
```

The sudo su - command is essentially the same as operating all commands as sudo. Then you will create a directory for the hard drive, mount it, and then change to it. From here, you will be able to use the cp command to copy all of your files, ie:
```
mkdir /home/<username>/VistaBackup
cp "/media/hda1/Documents and Settings/<username>/My Documents/" /home/<username>/VistaBackup
```
Once again, you are making a directory for files, then copying your files over. Note: The quotes are nessicary for any paths with spaces in them, such as Program Files or My Documents. Note: You cannot run the files in Ubuntu without an emulator or other runtime environment, like WINE.  Don't bother.

You can use a CD burner now to burn these files to a CD (actually, you can do that without copying to Ubuntu first if you wish). Now you can reinstall Vista.

NOTE:
You can create a link to the files on your desktop. Execute the first three commands, then type:
```
ln -s /media/hda1 /home/<username>/Desktop/Vista
```
Now a link on your Desktop, called Vista, will appear. You can open the folder and work on it from there, by copying the files using your CD Burner, or by copying them into another folder.

---

### Post by bijanv on 2007-02-07
okay so after reinstalling i can run GRUB loader but again choosing Vista just reboots

After doing ```
sudo nano -w /boot/grub/menu.lst
```

and looking under the Windows Vista section, this is what I see:

```
title    Windows Vista/Longhorn (loader)
root    (hd0,0)
savedefault
makeactive
chainloader +1 
```

and after entering ```
sudo fdisk -l
```

I see 3 partitions:

```

/dev/sda1       HPFS/NTFS
/dev/sda2       Linux
/dev/sda3       Linux swap / Solaris

```

---

### Post by aberry5555 on 2007-02-07
ok, so dev/hda1 is your vista partition and, what the GRUB is trying to do is tell it to load the bootloader on hd0,0 which happens to be your GRUB, so it just loops back on to itself. I don't think theres a way to insert the Vista boot information in to grub, unfortunately, but I think you can make vista link itself to the GRUB if the GRUB is installed on the second partition.

---

### Post by bodhi.zazen on 2007-02-07
Grub is fine as far as the windows root.

FYI the MBR = (hd0) and the windows partition is (hd0,0) (Grub starts counting with 0 )

Try this :

title    Windows Vista/Longhorn (loader)
**rootnoverify**    (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by bijanv on 2007-02-07
I tried intputting rootnoverify however the same thing happens.

It just loops back to GRUB loader.


aberry5555, how would I go about making vista link itself to GRUB?

---

### Post by bodhi.zazen on 2007-02-07
Try this grub entry then (I missed you have sd)

title Windows Vista/Longhorn (loader)
rootnoverify (sd0,0)
savedefault
chainloader +1

---

### Post by bijanv on 2007-02-07
hmm now after I select Vista I get the following error:

"Error 23: Error while parsing number

Press any key to continue..."

Pressing any key takes me back to the GRUB list

---

### Post by bodhi.zazen on 2007-02-07
This error is basically bad data, like entering the letter O rather then the number 0

Of course it could be we need to go back to (hd0,0) :lol:

Check you syntax

If that fails, well you can try adding the chainloader +1 back in as well ;)

And would you also post your Ubuntu stanzas ...

---

### Post by bodhi.zazen on 2007-02-07
I'll check in with you later ;)

here is a link that should help : [http://www.pro-networks.org/forum/about78184-0-asc-0.html](http://www.pro-networks.org/forum/about78184-0-asc-0.html)

---

### Post by bijanv on 2007-02-07
syntax seems fine, nothing that I can see

as for my ubuntu stanzas they go something like this (sorry I can't post the whole thing as I'm just retyping what I see from my laptop)

```

title   Ubuntu, kernel 2.6.17-10-generic
root   (hd0,1)
kernel /boot/-------------  <-- whole bunch of stuff :)
initrd   /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title   Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root   (hd0,1)
kernel /boot/-------------  <-- whole bunch of stuff :)
initrd   /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title   Ubuntu, memtest86+
root   (hd0,1)
kernel /boot/memtest86+.bin
quiet
boot


```

---

### Post by bodhi.zazen on 2007-02-07
Well it looks like you need to go back to root (hd0,0) ...

Try it without chainloader

---

### Post by bijanv on 2007-02-07
without chainloder, when I press enter on vista it does nothing

I had a moment of success when I removed savedefault and makeactive... I "think" it started to boot but then just hanged there.. when I rebooted, I went back to the same problem of it looping

---

### Post by bodhi.zazen on 2007-02-07
I'm at a loss.

My only other thought is to look at Supergrub :

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by bijanv on 2007-02-07
yes I know this is very strange... I thank you for all of your sincere help, I really appreciate that someone took their time to help me. 

I am only left with the only option to just backup my files from vista and do a clean format of my whole drive.

Hopefully I'll try installing ubuntu after this nightmare once people get a bit more adjusted to Vista.

---

### Post by bodhi.zazen on 2007-02-07
Well, I assume that means you tried supergrub ...

If not IMO it is worth a try before you back up and re-install 



Also, you could try the Micosoft forums, :tongue:

Be sure to ask them why vista can not boot with grub ](*,)

---

### Post by Herman on 2007-02-08
Hello bijanv and bodhi.zazen
>  I had a moment of success when I removed savedefault and makeactive... I "think" it started to boot but then just hanged there.. when I rebooted, I went back to the same problem of it looping  What do you mean exactly by 'looping'? If you mean you have a Grub Menu and you select Windows Vista and your monitor blinks and returns you to the same Grub menu?
When this happens it can mean that Grub is (accidentally) installed in the first sector of the Windows partition. So grub is chainloading the correct sector on your hard disk, but when it does, that simply points back to grub again.
I am not sure if this could possibly be the problem in this instance or not, but that is one way to produce that exact behavior.
There could be more than one cause for the same symptoms though. Grub should be installed the MBR or the Ubuntu partition's first sector or both, but not in the first sector of the Windows partition.
The most common cause of that is people using the grub-install command incorrectly, but I'm not saying that's what happened in this case.
Maybe I'm totally wrong here, but if that's a possibility, it's something to think about anyway. If you had Windows XP, I would advise trying the recovery console and FIXBOOT, but as it's Vista I don't know what you should do. I wish I could help more than this. I don't know much about Vista.
Regards, Herman

---

### Post by bodhi.zazen on 2007-02-08
Herman, thank you for the information.

---

### Post by marc_c on 2007-02-10
I am suffering similar Vista troubles:

I recently purchased a Toshiba Satellite A135-S4467 (Intel Core 2 Processor T5200, 1GB SDRAM,160GB HDD) and leaped into installing linux without looking  ....  resizing the Vista partition using GPARTED when installing Edgy from the Live CD.  

Below is my partition table.  I created multiple LINUX partitions to multi-boot with various flavors; however, post Ubuntu install, when I went to boot into Vista, I encountered errors and tried to recover using on screen Vista recovery instructions.  Anyhow after it ran for about 3 hours with no apparent progress, I did a hard shut down.  This morning, thinking I would start from scratch, I pulled out the Vista  recovery CD and followed the instructions for a full system recovery.  Upon boot, I get "Windows is loading files" with a progress bar.  Once complete, it displays the 'normal' boot splash screen for a few seconds and then just goes to a blank screen with no disk or screen activity.  

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        5413    41942898+   7  HPFS/NTFS
/dev/sda3            5414       19457   112808430    5  Extended
/dev/sda5            5414        8024    20972826   83  Linux
/dev/sda6            8025       10635    20972826   83  Linux
/dev/sda7           10636       13246    20972826   83  Linux
/dev/sda8           13247       13507     2096451   82  Linux swap / Solaris
/dev/sda9           13508       19457    47793343+   b  W95 FAT32

```

My thought is that the multiple partitions may be driving the Vista installer nutso.  Any ideas on how I can recover?

---

### Post by marc_c on 2007-02-10
Fixed my problem by following this post:

[http://ubuntuforums.org/showthread.php?t=346780&highlight=vista+recovery](http://ubuntuforums.org/showthread.php?t=346780&highlight=vista+recovery)

Cheers, Marc

---

### Post by teaker1s on 2007-02-10
[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx]("http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx")


[http://www.users.bigpond.net.au/hermanzone/]("http://www.users.bigpond.net.au/hermanzone/")

has vista specific duel boot info

---

