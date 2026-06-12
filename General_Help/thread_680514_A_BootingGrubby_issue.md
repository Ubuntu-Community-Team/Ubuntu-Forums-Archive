---
title: "A Booting/Grubby issue"
date: 2008-01-28
forum: General Help
---

### Post by MisterOnion on 2008-01-28
Hi everyone

I wasn't able to find a post that *quite* matched my big problem, so I thought i'd summarize it here:

I just installed Gutsy Gibbon using the Live CD onto a new partition of my C:\ drive. (Windows XP is on the 1st partition, i don't want to delete it)

However, I never noticed, nor was prompted over GRUB installation.
When I tried to start up, no OS was found... so I started up the Gutsy Live CD and did:
--------------
sudo grub
find /boot/grub/stage1
//which returned (hd1,1). Since my C:\ is SATA and i have a storage IDE, it's quite possible //hd1 is C:\, rather than hd0 ..?), then....
root (hd1,1)
setup (hd0)
quit
---------------
this did nothing on restart, so I replaced setup(hd0) with setup(hd1). 
Now on restart, a bare grub interface starts up with the correct options,
 however, none of them work!
Neither Ubuntu, nor the Windows XP which says 'NTLDR missing'.
(I can, however, start Windows using the Gnome partition manager boot CD option)

So now I thought I needed to fix the /boot/grub/menu.lst,
but the /grub/ folder does not exist! 

Thinking that i needed to install it from scratch, i tried in a terminal:

********
sudo apt-get install grub
// returned message: 'grub is already the newest version'
//so i did...
sudo grub-install /dev/hda
********
but I get: 'could not find device for /boot: Not found or not a block device'

i tried every other device hd* in the /dev/ folder.... same thing.

I know I'm a bit far off getting it to work properly, since
 i still haven't got a /grub/menu.lst or equiv. file to edit.

Please help me, I'm perhaps a bit new to all this...

Kind Regards,
Onion

---

### Post by rysh on 2008-01-28
When booting the Live CD ... open a terminal and do sudo fdisk -l /dev/sda and /dev/sdb etc ... and see what your boot device is! ... 

The entry in my /boot/grub/menu.lst which let Ubuntu boot is:

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=9b8b360b-ac7e-4850-a492-3516e9062306 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

The big number (UUID) for the partition identification you see, you can find with the program vol_id (maybe need to be used with sudo)

I see you tried sudo grub-install /dev/hda ... but in Ubuntu (gutsy) all devices are seen as SCSi devices So i think you should use /dev/sda 
Maybe you installed Ubuntu on your IDE device ? ... Or maybe installed grub on there and this is not the first device which boots ... 


hope this info helps ..

---

### Post by MisterOnion on 2008-01-28
Thanks, Rysh

Thanks for the tips! I found sda2 as the Ubuntu boot drive and sda1 as the XP boot drive.
However, I am still at a loss as how to install GRUB. I want to alter the menu.lst file so that 
it looks at the correct drives and boots correctly, however, my grub folder is sadly lacking in such a file.
doing:
sudo grub-install /dev/sda2 

results in another error to find block device.

Thanks again,
Onion

---

### Post by rysh on 2008-01-28
Hi ... 

Your "grub-install /dev/sda2" would try to install grub in the first sector of the linux partition.  Then when the computer boots the windows boot manager still doesn't know about the linux partition. 

Boot with the live cd
Open a terminal window
With df you can see if the linux partition is mounted 
if yes:
sudo chroot /dev/sda2 /media/sda2  
sudo dpkg-reconfigure grub

when you install grub in the mbr it can load windows and linux ... 

otherwise i would suggest:

Try to re-install with the alternate install cd ... this is a lightly modified debian text based installer and i think it works better.

The part when it should install grub is just after the installation of the packages is finished.

good luck.

---

### Post by perixx on 2008-01-28
Hy rysh...

about re-installing Ubuntu: will this also fix his problem with the missing 'ntldr'? Or will he have to perform 'fixboot' from the XP recovery console first?

perixx

---

### Post by rysh on 2008-01-28
The message from missing NTLDR is from Windows ... I am not sure if fixboot will fix this problem for him. ... But because Windows only thinks about itself it is advisable to try this first ... Then can try to install grub in the MBR ... grub-install /dev/sda .... (not sda2)

---

### Post by MisterOnion on 2008-01-28
Yea, im getting very worried and scared now, i don't want to have to reformat.
I cant access Xp at all now, not even from the Gnome Partition manager CD.

Got a link there for the alternate install CD? (the one with Grub and packages?)
it would be really nice to know if reinstalling Ubuntu and Grub properly will fix the XP MBR so that i dont get the missing NTLDR error. Incidentally, the Linux boot error is:
'Error 22: No such partition' perhaps further evidence that it is not installed properly.

Onion

---

### Post by MisterOnion on 2008-01-28
Ok: so to summarize, what is the best procedure?

try to run fixboot to repair the MBR, and
then run the alternative Ubuntu CD and install over the partition where i tried before?

Or is it worth persisting with trying to get GRUb working here and now?
sudo grub-install /dev/sda does not work

Onion

---

### Post by rysh on 2008-01-28
> Yea, im getting very worried and scared now, i don't want to have to reformat.
I cant access Xp at all now, not even from the Gnome Partition manager CD.

I think it is not strange you can not boot Windows XP with a "Gnome Partition Manager CD". 


> Got a link there for the alternate install CD? (the one with Grub and packages?)

[http://mirrors.kernel.org/ubuntu-releases/gutsy/ubuntu-7.10-alternate-i386.iso](http://mirrors.kernel.org/ubuntu-releases/gutsy/ubuntu-7.10-alternate-i386.iso)

> it would be really nice to know if reinstalling Ubuntu and Grub properly will fix the XP MBR so that i dont get the missing NTLDR error. 

You already got this error message when trying to boot Windows?
If yes... try to 'fixboot' Windows first. 

> Incidentally, the Linux boot error is:
'Error 22: No such partition' perhaps further evidence that it is not installed properly.


Is this after the grub boot menu? or you do not see any menu? .... If the last one and you indeed have seen the NTLDR error message from Windows, i recommend to try to fixboot windows first

---

### Post by rysh on 2008-01-28
> try to run fixboot to repair the MBR, and
then run the alternative Ubuntu CD and install over the partition where i tried before?

That's indeed an option. I think this will at least let you have windows back ... and this is i guess the most important for you now. 

> Or is it worth persisting with trying to get GRUb working here and now?
sudo grub-install /dev/sda does not work

and when you "sudo dpkg-reconfigure grub" ?

You can try to reconfigure grub first and then try to load Windows XP from the /boot/grub/menu.lst .... with this entry:

title Windows 
root (hd0,0)
makeactive
chainloader +1

---

### Post by MisterOnion on 2008-01-28
I see these boot errors after the grub menu. The grub menu is there and seems fine.
Just none of my OS's will boot.

I was trying to install some packages I may need for Ubuntu but was not able to do yum update.
when I tried to install yum, I have to enable component called 'universe'.

If the fixboot fails to fix the MBR, does that mean I have to reformat both the XP and linux partitions?

Onion

---

### Post by rysh on 2008-01-28
> I see these boot errors after the grub menu. The grub menu is there and seems fine.
Just none of my OS's will boot.

Then it seems grub is indeed installed in the MBR and the menu.lst is available otherwise you won't see a "grub-menu" 

when in the boot menu you can try to use "e" to edit any line of the grub menu ... 
Maybe there is something wrong with which is "hd0,0" and "hd0,1"



> I was trying to install some packages I may need for Ubuntu but was not able to do yum update.
when I tried to install yum, I have to enable component called 'universe'.


Yum is a package manager from Fedora ... Ubuntu is Debian based and uses "apt" To update you then do "apt-get update" and "apt-get upgrade" 

> If the fixboot fails to fix the MBR, does that mean I have to reformat both the XP and linux partitions?

I think in the case of failing to 'fixboot' windows, it looks like you need to re-install windows ... but i recommend you to try to make linux working, because you have at least grub with a grub menu installed ... I have seen before also on my own machines there is sometimes a mistake in what is hd0,1 or hd1,1 ... 

You said you have two HD's .. one PATA and one SATA ? ... maybe grub makes a mistake and thinks it need to find the OS's on you PATA disk

---

### Post by perixx on 2008-01-28
I've yet to see an XP installation I can't get back to live due to overwritten MBR code. Only thing I can think of is when you wipe the PARTITION TABLE. Should 'fixboot' alone in the recovery console of XP not work, try also 'fixmbr'. That'll save your day in 95% of all cases.

Seriously, I have some links here, even for the infamous 'NTLDR missing' issue but I'm too tired to dig out now out of hundreds of links... tomorrow.

regards,
perixx

---

### Post by perixx on 2008-01-29
I'd like you to have a look at this greatly sophisticated Grub page at '**[COLOR="Teal"]Hermanzone's[/COLOR]**' - it contains a fantastic troubleshooting section and provides tons of useful information on booting - probably all you'll ever need:
> [http://users.bigpond.net.au/hermanzone/p15.htm#12_]("http://users.bigpond.net.au/hermanzone/p15.htm#12_") 
For the NTLDR-issue see: [http://tinyempire.com/notes/ntldrismissing.htm]("http://tinyempire.com/notes/ntldrismissing.htm")


[COLOR="RoyalBlue"]**_Great little helpers in case of trouble:_**[/COLOR]

**Ultimate Boot CD 4 Windows**
[http://www.ubcd4win.com/]("http://www.ubcd4win.com/")
**Ultimate Boot** - NOT THE SAME (!)
[http://www.ultimatebootcd.com/]("http://www.ultimatebootcd.com/")
**Super Grub Disk** - boot any system - a little difficult for newbies
[http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

Also very interesting for newcomers, though I haven't used it myself - easy multi-booting:
[http://www.icpug.org.uk/national/linnwin/contents.htm]("http://www.icpug.org.uk/national/linnwin/contents.htm")

regards,
perixx

---

