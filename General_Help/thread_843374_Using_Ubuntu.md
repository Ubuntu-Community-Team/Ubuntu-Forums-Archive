---
title: "Using Ubuntu"
date: 2008-06-28
forum: General Help
---

### Post by umeshpr on 2008-06-28
Just received my free CD of Ubuntu (Yippee!!!)

I am clueless. I am an absolute newbie.

1.I have a wireless dial-up connection. It says most Ubuntu does not support most dial-up connections.

does that mean i cannot connect to the net?  :(

2.Can I have two Operating Systems installed & choose on start-up which to use without affecting any of my files/folders in the desktop?

3.Can i run Ubuntu from my CD drive and surf normally (access my files/folders, save from the net into my files/folders)?


Plz read my questions & anybody reply as if explaining to a baby( coz I am one :confused:)

---

### Post by rraj.be on 2008-06-28
> **umeshpr said:**
> 
1.I have a wireless dial-up connection. It says most Ubuntu does not support most dial-up connections.


i am too using dial up connection and every Ubuntu Supports dial up connection
> 
2.Can I have two Operating Systems installed & choose on start-up which to use without affecting any of my files/folders in the desktop?


sure .

Look at here.

```
[http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
```


> 
3.Can i run Ubuntu from my CD drive and surf normally (access my files/folders, save from the net into my files/folders)?

Sure


For further info go here.

You will get every thing you needed.

```
[http://www.psychocats.net/ubuntu/]("http://www.psychocats.net/ubuntu/")
```

You can post any doubt here and you will get solution within 5-minutes

---

### Post by umeshpr on 2008-07-29
Thanks.

---

### Post by umeshpr on 2008-07-30
I installed  Virtualbox and tried to install Ubuntu inside it as per the instructions on the psychostats.

when the installation reaches about 75% it says disc space insufficient on /target.

what should i do? :(

I have 160gb HDD (c:76 d:76) 1gb RAM

I had allocated 512mb RAM to Ubuntu in Virtual box.

---

### Post by Vorian Grey on 2008-07-30
You need to give it more disk space. Go into settings to adjust it.

---

### Post by Mgiacchetti on 2008-07-30
>>>If you only have ubuntu installed and dont want to reinstall ubuntu but learn more complex commands

forget virtualbox and delete the virtual drive(s) you created with it to save space.

get the Gparted ISO from [here]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779") and burn it to a disk after downloading. 

now [read this]("http://gparted.sourceforge.net/larry/resize/resizing.htm") and understand you want to shrink your ubuntu disk, so windows can be installed.   and [this]("http://ubuntuforums.org/showthread.php?t=358183&highlight=windows")  for information on how to install winodws after ubuntu has been installed   READ THIS FULL PAGE!



**[COLOR=Red]!!ATTENTION!![/COLOR]**
>>>installing a dual boot system in this order is backwards, if you can stand reinstalling ubuntu, follow as below.

1> Format your first partition and install windows to it.

2> Format your second partition and install Ubuntu to it, using the manual partition option in the setup. (be sure to choose your mountpoint, and make a swap drive)

3> You will need to install the GRUB onto the ubuntu drive, to do this, at the last step (the page with the summary) you should see an advanced button, click it and opt to install GRUB on the drive that you are installing ubuntu on, and go ahead and begin the installation.   reboot when finished.

If you have followed step 3 correctly, skip step 4.

4> If you run into problems with not being able to boot back into windows... (you installed GRUB on the MBR by accident)

4.1> grab your windows disk
4.2> act like you are about to install again
4.3> when prompted hit "R" for recovery console
4.4> login to your windows install and type ```
fixmbr
```
4.5> [FONT=Verdana]Now, to get your grub installed on the correct drive, you need to read [this]("http://ubuntuforums.org/showthread.php?t=224351")[/FONT], return when you are done.


5> Now that you have windows working, its time to get ubuntu working. 

Get [this]("http://www.winimage.com/bootpa26.zip") and unzip it to c:\
go Start > run > cmd
press enter
type ```
cd \
``` and press enter

type ```
bootpart
```this will list all of your partitions,  your looking for linux native or ext3
it should look something like this:
```

C:\>bootpart.exe
ˆBoot Partition 2.60 for WinNT/2K/XP (c)1995-2005 G. Vollant (info@winimage.com)
WEB : http://www.winimage.com and http://www.winimage.com/bootpart.htm
Add partition in the Windows NT/2000/XP Multi-boot loader
Run "bootpart /?" for more information

Physical number of disk 0: ffff6a32
0 : C:* type=42 , size=22659651 KB, Lba Pos=63
1 : C: type=42 , size=17358232 KB, Lba Pos=45319365
Physical number of Disk 1 : ca1dca1d
2 : D: type=83 <Linux native>, size=6184993 KB, Lba Pos=63
3 : D: type=82 <Linux swap>, size=522112 KB, LBA Pos=12370050
4 : D: type=83 <Linux Native>, Size=1542240 KB, LBA Pos=13414275

```so lets say that [FONT=Verdana]my grub is on 2 i would type at c:\>

```
bootpart 2 LBA ubuntu.lnx Ubuntu
```It will do its thing, and grab the ubuntu boot info, and add the corresponding line to boot.ini
you can check this by typing 

```
bootpart list
```go ahead and restart now. you should see ntldr come up asking for Windows XP or Ubuntu (note:  you still have grub as well for your different linux kernels, but you can delete the windows reference(s) in grub, because ntldr takes care of that)
[/FONT]```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup
gksudo gedit /boot/grub/menu.lst

```and comment out (or delete) from
# This is a divider, added to separate the menu items below from the Debian

to the bottom and save and close.

---

