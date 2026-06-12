---
title: "HOWTO: Running Windows programs under Edgy/Feisty with a virtual (or physical) box!"
date: 2007-02-14
forum: General Help
---

### Post by DARKGuy on 2007-02-14
Do you want to do... this?

[IMG]http://img468.imageshack.us/img468/7913/omg2kg0.jpg[/IMG]

Then you're in the right place!

Greetings!

Alright, this is my first HowTo so please be nice to me XD! ... ^^; anyways. After searching around for so long how to run windows apps "correctly" under Linux without stuff like WINE / Cedega / Mono (awesome projects though!), I came around a [**_thread_**]("http://ubuntuforums.org/showthread.php?t=358968") by TR3GO asking how to run Windows apps in Linux. He posted a [**_link_**]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") to the community docs about running Windows XP under Qemu and then running Windows apps in that virtual machine like if they were daemons, but getting the result on your screen. Sadly, it was only for Feisty, and I wanted to do it on Edgy, and so my journey began...

**DISCLAIMER: **This guide is based mainly on the Community Help link [**_here_**]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") and some text may have been taken from it for the sake of not saying the same thing the guide says with other words :P, It's also based in other articles found in the internet. 

[COLOR=Red][SIZE=3]**This guide is for EDGY users. Feisty Fawn users go [_here_]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") instead!**[/SIZE][/COLOR]

[COLOR=Red]**[SIZE=5]Step 1: Installing a virtualization program[/SIZE] - (Skip this if you have a physical Windows box around)**[/COLOR]

[SIZE=3]**Using QEmu + KQEmu**[/SIZE]

QEmu is a PC virtualization program, similar to VMWare but free, and as such, it requires a module (KQEmu) for increased speed.
[LIST=1]
[*]We've got to install Qemu, and some building tools for building the KQEmu module. Open a terminal and type: ```
sudo apt-get install qemu build-essential linux-headers-`uname -r`
``` [COLOR=Blue]I might be missing some packages here, since my setup is already set with development packages, so if you find there are missing packages please tell me so I can add them here.[/COLOR]
[*]After QEmu is installed, we need to download the KQEmu module [**_here_**]("http://fabrice.bellard.free.fr/qemu/kqemu-1.3.0pre11.tar.gz")
[*]Then, in the same terminal if you wish, type the following: ```
tar xvvf kqemu-1.3.0pre11.tar.gz
cd kqemu-1.3.0pre11
./configure
make
sudo make install
```That should do it.
[*] Now, we should create a virtual disk for installing Windows XP into: ```
qemu-img create -f qcow windows.img 2G
```[quote="Feisty guide"]This creates a two gigabyte virtual drive, stored as a single file called windows.img in the location where you ran the command. Any size above 1.5GB (the minimum to run Windows XP) is fine. The virtual drive will start out as a small file, and only fill its the size you specified when it reaches capacity due to the 'qcow' file format used.

**Note:** If you use qcow images, you will not be able to mount the image within Ubuntu. You can omit '-f qcow' and create a mountable image, but this will mean that the size of the virtual drive will be fixed and larger. Instructions to convert a raw drive to a qcow drive appear at the end of [**_this_**]("https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo") page.[/quote]
[*]We've got to activate KQEmu, then run QEmu with out XP CD inserted so it boots from the CD and starts installing. ```
sudo modprobe kqemu
sudo mknod /dev/kqemu c 250 0 
sudo chmod 666 /dev/kqemu
[COLOR=Blue]sudo umount /dev/shm
sudo mount -t tmpfs -o size=400m none /dev/shm[/COLOR]
<insert Windows XP CD>
sudo mount /dev/cdrom
qemu -localtime -cdrom /dev/cdrom -m 384 -boot d windows.img
```Or, if you're using an ISO:
```
qemu -localtime -cdrom cdimagefile.iso -m 384 -boot d windows.img
```I'd recommend 256Mb or 128Mb, contrary to the author of the Feisty guide, since it's going to be virtualized inside your computer and taking RAM from it. If you have a low-end PC like mine (933Mhz, 256Mb RAM) you can change 384 by 128, it runs alright anyways and consumes less ram. **However, for the sake of the tutorial, we'll be using 384Mb for the QEmu machine.**

The stuff in blue is related to the error you might get below, so it's better to be prepared:

* If you're running 384Mb in QEmu, sudo mount /dev/shm with 400m
* If you're running 256Mb in QEmu, sudo mount /dev/shm with 272m
* If you're running 128Mb in QEmu, sudo mount /dev/shm with 142m

**Note:** If it complains about not having enough memory or something similar to this error below, then follow the instructions above, highlighted in blue: [quote="Nasty error"]You do not have enough space in '/dev/shm' for the [COLOR=Blue]384[/COLOR] MB of QEMU virtual RAM.
To have more space available provided you have enough RAM and swap, do as root:
[COLOR=Blue]umount /dev/shm
mount -t tmpfs -o size=400m none /dev/shm[/COLOR]
Or disable the accelerator module with -no-kqemu[/quote]

[quote="Feisty guide"]**Note to 64 bit users:** Use 'qemu-system-x86_64' instead of 'qemu'. Otherwise the "-kernel-kqemu" option will not work.

**Note for Windows 2000: **Add the option '-win2k-hack'. Otherwise the install may fail with "Not enough disk space" even when that isn't the case. 
[/quote]

All that is left is installing Windows XP as you normally do. Clicking on the QEmu window will take control of the Windows cursor. To go back to Linux, press Ctrl + Alt.

You can also toggle fullscreen with Ctrl + Alt + F.

**[COLOR=red]AFTER IT'S FINISHED:[/COLOR]**

When your XP installation has finished and you're back in the desktop ready to rumble, the next time you're going to run the VM for remote application purposes which is the object of this guide, you **MUST** run QEmu this way:```
qemu -localtime -m 384 -redir tcp:3389::3389 windows.img
```. [quote="Feisty guide"]This sets up some networking options - making any connections to the localhost port 3389 be directed to the VM on port 80, where Windows Terminal Services will run.[/quote]

**NOTE:** VMWare users DON'T need to do this, obviously.[/LIST]
[COLOR=Red]**[SIZE=5]Step 2: Installing rdesktop 1.5 in Edgy[/SIZE]**[/COLOR]

Quite easy, just follow this guide: _**[http://www.ubuntuforums.org/showthread.php?t=224212](http://www.ubuntuforums.org/showthread.php?t=224212)**_ - or, alternatively, you can just open a terminal and type (taken from the same guide):```
sudo apt-get install rdesktop openssl libssl-dev libx11-dev
wget http://howtoforums.net/downloads/rdesktop-1.5.0-rc1.tar.bz2
tar -xjf rdesktop-1.5.0-rc1.tar.bz2
cd rdesktop-1.5.0-rc1
./configure
make
echo "backup rdesktop original";sudo cp -vp /usr/bin/rdesktop /usr/bin/rdesktop1.4BKUP
sudo mv /usr/bin/rdesktop /usr/bin/rdesktop1.4
sudo make install
sudo chmod +x /usr/local/bin/rdesktop
sudo ln -s /usr/local/bin/rdesktop /usr/bin/rdesktop
```Then validate the install: ```
rdesktop 2>&1 | grep Version
```It should say something like this: ```
Version 1.5.0-rc1. Copyright (C) 1999-2005 Matt Chapman.
```[COLOR=Red]**[SIZE=5]Step 3a: Configuring Windows XP[/SIZE]**[/COLOR]

Alright, Windows is already installed. What now? we've got to configure it for allowing remote access!.

**Note: ** My Windows is in Spanish, so I'm sorry for the Spanish screenshots :/. If anybody got a copy of Windows XP SP2 in English and could take the same screenshots, I could add them here for better understanding of the HowTo.
[LIST=1]
[*]Go to **Start -> Control Panel -> User Accounts** ([IMG]http://img365.imageshack.us/img365/883/screenshot2007021414490qo2.jpg[/IMG])
[*]There, you can use the chance to make another user with Administrative privileges so you can run everything without problems. Anyways, click "Change the way the users log in"
[IMG]http://img400.imageshack.us/img400/2517/screenshot2007021414480mv8.jpg[/IMG]
[*]Now, we have to allow the Welcome Screen, and Fast User Switching:
[IMG]http://img518.imageshack.us/img518/4816/screenshot2007021414480mq4.jpg[/IMG]
[*]Close the window, and in the **Control Panel**, go to **System** now ([IMG]http://img443.imageshack.us/img443/1859/screenshot2007021414485gj2.jpg[/IMG])
[*]There, go to the **Remote** tab, click **"Allow users to connect remotely to this computer"** then click **Ok**:
[IMG]http://img523.imageshack.us/img523/5002/screenshot2007021414500nk0.jpg[/IMG][/LIST]
There's just two steps left, quite easy to this point, no?

[COLOR=Red]**[SIZE=5]Step 3b: Configuring Windows 2000 Server[/SIZE]**[/COLOR]

No idea yet, I'm installing W2k server in a 133Mhz/48Mb RAM, 61% in about 2 hours :/ so it's still installing as I type this.

[COLOR=Red]**[SIZE=5]Step 4: Installing the required software in the server machine or guest OS[/SIZE]**[/COLOR]

Download **_[http://www.cendio.se/files/thinlinc/seamlessrdp/seamlessrdp.zip](http://www.cendio.se/files/thinlinc/seamlessrdp/seamlessrdp.zip)_**.

Extract it to **C:\seamlessrdp** or something similar, a short path without spaces or long names preferably. After it's extracted, just log out the VM (or the user session in your physical box).

[COLOR=Red]**[SIZE=5]Step 5: Testing![/SIZE]**[/COLOR]

You can make yourself a script, or just run this directly from the terminal:

**Running from a VM with QEmu:** ```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" localhost:3389 -u username -p password
```**Running from a Physical Windows PC or VMWare:** ```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" [COLOR=Blue]255.255.255.255[/COLOR] -u username -p password
``` (just change 255.255.255.255 by the computer's real IP, or if you're running VMWare, go to **Control Panel -> Network Connections -> Double Click the VMWare connection in there -> Go to the Support tab -> click Details -> Where it says "IP Address", that's what you're going to use** (thanks aktiwers!)).

If it works, voilá! you can run remote apps in Linux, without the need for WINE, Crossover Office, Cedega, Winetools, etc...

[COLOR=Red]**[SIZE=5]Scripts for running various programs[/SIZE]**[/COLOR]

Alright, I'm gonna explain a bit of the rdesktop functions and give you all some example scripts for running other programs (requested by aktiwers ^^). By typing "man rdesktop" you can see some of the parameters you can use. I haven't used them all but I'll explain a few useful ones I know:
[LIST]
[*]**-d domain**[INDENT]This sets the domain used for authentication, in case your PC/the server isn't/are under a domain.[/INDENT]
[*]**-s "command"**[INDENT]This runs "command" in the remote computer instead of Explorer.exe. You **don't** need to run Explorer.exe because then it will replace your current desktop and be over everything else (well in some WMs you can move the window to a desktop layer like Fluxbox, but it isn't the idea either :/, at least not for this HowTo xD). Running -A -s with seamlessrdpshell.exe does the trick of setting the other parts of the desktop transparent (the seamlessrdpshell.exe and -A does that). Without -A and seamlessrdpshell.exe together, you'll get a big remote desktop like VNC, but fullscreen.[/INDENT]
[*]**-c directory**[INDENT]This suppossedly sets a "home" directory for the remote apps to run. I have no idea, however, if this will have effect in physical Windows boxes. It seems to work in VMs like the author of the Feisty guide says.[/INDENT]
[*]**-k**[INDENT]This sets a keyboard layout to emulate. I need to use "-k es" because I have a Spanish keyboard :P[/INDENT]
[*]**-a bpp**[INDENT]Sets the display depth for the RDP connection to be displayed in your X screen. bpp can be 8, 15, 16 or 24 (bpp stands for bits-per-pixel).[/INDENT]
[*]**-rsound**[INDENT]This will redirect sound from the remote machine to yours. This way you can use WinAmp, WMP and other stuff that require sound and hear it locally.[/INDENT][/LIST]
**Useful scripts (Windows XP):**

Cmd (Command shell) ```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\windows\system32\cmd.exe" IPADDRESS -u username -p password
```Internet Explorer ```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\program files\internet explorer\iexplore.exe" IPADDRESS -u username -p password
```MSN Messenger ```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\program files\msn messenger\msnmsgr.exe" IPADDRESS -u username -p password
```Task Manager ```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\windows\system32\taskmgr.exe" IPADDRESS -u username -p password
```Adobe Photoshop CS2 ```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\program files\adobe\adobe photoshop cs2\photoshop.exe" IPADDRESS -u username -p password
```And you can make yours too! just **be sure to place the full command line between quotes!!! "" just like it's shown above, because it won't work if you don't!**

Here's a "general" script I made so you all can run programs by just specifying their path. You can save it as **rdesk.sh** if you want (don't forget to **chmod +x rdesk.sh** or else it won't run!):

```
rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe $1" IPADDRESS -u username -p password
```Just change IPADDRESS, username and password by the values you are required to input. The usage is: **./rdesk.sh "c:\windows\system32\cmd.exe"** :)

[COLOR=Red]**[SIZE=5]Final notes[/SIZE]**[/COLOR]

Alright, the procedure looks long and big, but it's really no rocket science: Just install the VM emulator, install XP, install rdesktop 1.5, configure XP and make your script! You could also do the same thing with VMWare, just use the VMWare machine's IP as if it was a physical box.

It's also a good idea to make a script to have a cmd.exe running (**c:\windows\system32\cmd.exe**) as primary app, because you can use that one for launching other apps in the remote machine. I noticed that the seamlessrdpshell.exe only runs **one** application at a time - I didn't like that :P so I run cmd.exe and launch the other apps directly from there.

3D stuff? kinda works, I was able to run MilkShape 3D in my mother's 950Mhz/256Mb RAM/WinXPSP2 box without problems, what you're really depending in here is the network speed and the responsiveness between your machine and the "server" one, but it works, like hell :D.

I hope this HowTo has been useful to you all. Questions, suggestions, regards, cursing and all that can be left here in this thread, I will answer ^^.

---

### Post by g3k0 on 2007-02-14
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ sudo chmod 666 /dev/kqemu
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ umount /dev/shm
umount: /dev/shm is not in the fstab (and you are not root)
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ sudo umount /dev/shm
umount: /dev/shm: device is busy
umount: /dev/shm: device is busy
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ mount -t tmpfs -o size=400m none /dev/shm
mount: only root can do that
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ ahh!

---

### Post by DARKGuy on 2007-02-14
> **g3k0 said:**
> zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ sudo chmod 666 /dev/kqemu
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ umount /dev/shm
umount: /dev/shm is not in the fstab (and you are not root)
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ sudo umount /dev/shm
umount: /dev/shm: device is busy
umount: /dev/shm: device is busy
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ mount -t tmpfs -o size=400m none /dev/shm
mount: only root can do that
zaccheus@geckoLaptop:~/Desktop/kqemu-1.3.0pre11$ ahh!

Oh, forgot to add the sudo before mount and umount ¬¬ just fixed it, thanks :P

It's weird anyways, are you running apps that are taking shared memory / swap ? try doing it with a fresh reboot or log out and log back in to see if that makes any change o.o; Also, it says something about /dev/shm not being in fstab. Do you have a swap partition enabled? by typing "top" in a terminal you can check:

[quote="top"]Swap:   746980k total,      196k used,   746784k free,   102236k cached[/quote]

If it says something like Swap:     0 total, 0k used, etc... it means you don't have swap activated. 

Try activating it using gparted with an Ubuntu LiveCD. I don't recall the exact commands but IIRC, you have to mount your linux drive with read/write permissions and use gparted to format the swap partition and make it a swap one again, at least that solved it for me, but you've got to have **real careful** as you're editing the partitions in there :P

---

### Post by statictonic on 2007-02-14
Wow that's pretty sweet, I was wondering if there was a way to do this.  Haven't tried it yet, will try later, but thanks for the guide!

---

### Post by aktiwers on 2007-02-14
Ok.. I got it working with VMware.. Thanks! It works perfectly!
Could you post a few more commands how to open different programs?

Fx. Im trying to open MSN, I type:
```
rdesktop -rsound -A -s "c:\seam\seamlessrdpshell.exe C:\Program Files\Messenger\msmsgs.exe IPADDRESS -u username -p password
```But this doesnt open MSN, but it opens IE fine.. ?

EDIT:
Am I forgetting some "" or something?

Edit2:
Yes! it was a " after the msmsgs.exe..  nevermind! Thanks for a great HOWTO! :)

---

### Post by aktiwers on 2007-02-14
Photoshop CS2 running fine!

---

### Post by Vivix729 on 2007-02-14
Sweet guide.  May have to try this later. 

Dumb question though...what if the XP computer is behind a router?  How would you handle the IP address?

---

### Post by DARKGuy on 2007-02-14
> **aktiwers said:**
> Ok.. I got it working with VMware.. Thanks! It works perfectly!
Could you post a few more commands how to open different programs?

Fx. Im trying to open MSN, I type:
```
rdesktop -rsound -A -s "c:\seam\seamlessrdpshell.exe C:\Program Files\Messenger\msmsgs.exe IPADDRESS -u username -p password
```But this doesnt open MSN, but it opens IE fine.. ?

EDIT:
Am I forgetting some "" or something?

Edit2:
Yes! it was a " after the msmsgs.exe..  nevermind! Thanks for a great HOWTO! :)

XD sure, I'll post some more soon, glad to know it worked in VMWare! did you use the VMWare machine's IP right? just to clarify so I can test and add it to the guide too ^^;; What are your system specs and did you install VMWare+XP+CS2 or are you running a physical Windows box? By the way, cool CS2 ;)

> **Vivix729 said:**
> Dumb question though...what if the XP computer is behind a router?  How would you handle the IP address?

Hm, I haven't tinkered with routers yet, but I *guess* you'll have to redirect port 80 and 3389 to that machine (I'm not sure about the 80 one though). You can also open any port in the router directed to 3389 or 80 in the server machine and connect through it too: ```
rdesktop -rsound -A -s "c:\seam\seamlessrdpshell.exe C:\Program Files\Messenger\msmsgs.exe" IPADDRESS:PORT -u username -p password
``` *shrugs* it's worth a try.

---

### Post by llamakc on 2007-02-14
Thanks for the howto. Very nice. This will work great for stuff like iTunes (hopefully).

---

### Post by aktiwers on 2007-02-14
Yes I used the VmWare IP..  when you are in "Network connections" in XP, it has one called "Vmware connection" just double click it and check the IP there.

And yes, I installed VMWare+XP+CS2, though the Vmware+XP was an old install. But its all running on the same machine.

Maybe it wont be nessesery to add more programs, as people install them different places. Unless its another command?

Untill now this has worked fine for me (also with MSN Live Messenger)
```

rdesktop -rsound -A -s "c:\seam\seamlessrdpshell.exe [COLOR=Red]C:\Path\to\Progam.exe"[/COLOR] IPADDRESS -u username -p password
```

EDIT:
System Specs

AMD Athlon XP 2800+ 2083 Mhz

Asus A7N8X Deluxe Gold

Samsung PC3200, 1024 MB

NVIDIA GeForce 6200A / 400 MHz / 85 Hz / AGP 8x
256 MB GDDR2 SDRAM / 533 MHz

---

### Post by DARKGuy on 2007-02-14
> **aktiwers said:**
> Yes I used the VmWare IP..  when you are in "Network connections" in XP, it has one called "Vmware connection" just double click it and check the IP there.

And yes, I installed VMWare+XP+CS2, though the Vmware+XP was an old install. But its all running on the same machine.

Maybe it wont be nessesery to add more programs, as people install them different places. Unless its another command?

Untill now this has worked fine for me (also with MSN Live Messenger)
```

rdesktop -rsound -A -s "c:\seam\seamlessrdpshell.exe [COLOR=Red]C:\Path\to\Progam.exe"[/COLOR] IPADDRESS -u username -p password
```

Ah, good to know! I'll edit the HowTo right away :). Well, you're right, I just made a "general" script for running programs without typing so much in case some like to run stuff directly from a terminal :p

---

### Post by llamakc on 2007-02-14
Works for me too. Just tested with iTunes (image of empty iTunes library, VMWare & XP, on OpenBox).

---

### Post by DARKGuy on 2007-02-15
Cool! glad to know it worked :)

Now, anybody got around to doing this procedure with VirtualBox and Seamlessrdp? (Awesome program by the way, it runs with almost-native speed here, truly impressive and it doesn't lag the PC while it's running (contrary to QEmu or VMWare) :) *claps*), 'cause all I get is a remote desktop window on the top-left corner of the screen, but not any kind of remote login or anything like that when I try :(. I'm using XP SP2 by the way.

If anybody knows a way around this, I'd be toooootally glad :D

---

### Post by g3k0 on 2007-02-15
My xp install has been going since we landed on the moon(if we actually did) and the energizer bunny started going.

---

### Post by g3k0 on 2007-02-15
I finished installing but it goes soooooo slow in Qemu.  Is this normal?  I dont want to bother with rd if that will run equally slow.  One thing I couildnt do is the bue umount command.. That is probably related.  Help me get it going faster

sudo umount /dev/shm
umount: /dev/shm: device is busy
umount: /dev/shm: device is busy

Perhaps this is related too.  It works but goes slow

zaccheus@geckoLaptop:~$ qemu -localtime -m 384 -redir tcp:3389::3389 windows.img
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

---

### Post by DARKGuy on 2007-02-15
> **g3k0 said:**
> I finished installing but it goes soooooo slow in Qemu.  Is this normal?  I dont want to bother with rd if that will run equally slow.  One thing I couildnt do is the bue umount command.. That is probably related.  Help me get it going faster

sudo umount /dev/shm
umount: /dev/shm: device is busy
umount: /dev/shm: device is busy

Perhaps this is related too.  It works but goes slow

zaccheus@geckoLaptop:~$ qemu -localtime -m 384 -redir tcp:3389::3389 windows.img
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Weird, it isn't normal that it goes slow (well, depends on your system specs) but KQEmu doesn't seem to be loaded judging by the error it says when you open QEmu. Did you compiled KQEmu correctly? try following the points 2 & 3 from Step 1 and load KQEmu as shown in the 5th point, else it won't work.

About /dev/shm I have no clue :/ that never happened to me so :(

---

### Post by aktiwers on 2007-02-15
Its slow in Qemu for me too, thats why I use Vmware, where its fast as hell!
I really cant tell if its running windows only or as guest OS.. Fast as hell!

---

### Post by spockrock on 2007-02-15
Also I think this is how its supposed to work, but once I exit photoshop, ok any app acctually, I cannot open up the app again, until I log back into my windows xp, via vmware server,  then run explorer again, and then say run my the script for said application.                                                                                                                                         

and does anyone else get this problem while running photoshop where the area I highlighted does not work, until the app is rsized by a small amount??

[IMG]http://img.photobucket.com/albums/v605/redemma/xgl/photoshop.jpg[/IMG]

---

### Post by aktiwers on 2007-02-15
I had the same problem with photoshop, as you can see on my screenshot I removed that bar.

---

### Post by spockrock on 2007-02-15
ok thanks and the explorer thing??

---

### Post by DARKGuy on 2007-02-15
I guess you have to *log out* the session in XP so you don't have the explorer issue.

---

### Post by aktiwers on 2007-02-15
Yes, make sure you are logged out of XP (at the login screen), else you will have the explorer problem ( I had that as well). 

Its really just like running Remote control windows XP, if you ever done that? :)

---

### Post by spockrock on 2007-02-15
I am logged out, if I do not log out, I just the the full screen remote desktop window instead of the app, if I log out, then I get the app but explorer crashes..... :\


maybe its vmware tools thats causing it??

---

### Post by aktiwers on 2007-02-15
But I dont think explorer crashes.. it closes. As the whole idea with this, is to run the app outside of explorer. Else you could as well run it inside the virtual machine?

Does the app you run crash as well?

---

### Post by spockrock on 2007-02-15
no the app does not crash, apps run fine, the problem then is when explorer is closed I cannot, run the app again, unless I login, again restore explorer, and then run the the photoshop script for example again to get photoshop working again.  If I do try to run that app again I just get nice fullscreen window of my windows desktop.

---

### Post by brocktune on 2007-02-15
got this

brocktune@warmermilks:/bin/img$ qemu-img create windows.img 2G
Formating 'windows.img', fmt=raw, size=2097152 kB
qemu-img: Error while formatting


what gives?

---

### Post by chrish670 on 2007-02-15
I'd presume if I wanted to use Win98SE (in lieu of XP or 2000,) the procedure you've outlined thus far, would work as well or better as the XP install?  Reason for my question here is the software I'll be planning to run within a virtualized "windows" drive I wish to create on a laptop system.  

One program that is "iffy" is the Voodoo chat client.  I've heard it can work in some builds of Linux using WINE...  but I think this VM solution just may be the ultimate workaround.   There are some concerns. I only have 128MB of physical ram on laptop which I'm thinking I'll upgrade to 384MB (max for that laptop)

---

### Post by DARKGuy on 2007-02-15
> **spockrock said:**
> no the app does not crash, apps run fine, the problem then is when explorer is closed I cannot, run the app again, unless I login, again restore explorer, and then run the the photoshop script for example again to get photoshop working again.  If I do try to run that app again I just get nice fullscreen window of my windows desktop.

Whoah, that's a weird issue o_O... what version of XP are you running in the VM?

> **brocktune said:**
> got this

brocktune@warmermilks:/bin/img$ qemu-img create windows.img 2G
Formating 'windows.img', fmt=raw, size=2097152 kB
qemu-img: Error while formatting


what gives?

Did you try with the **-f qcow** parameter?

> **chrish670 said:**
> I'd presume if I wanted to use Win98SE (in lieu of XP or 2000,) the procedure you've outlined thus far, would work as well or better as the XP install?  Reason for my question here is the software I'll be planning to run within a virtualized "windows" drive I wish to create on a laptop system.  

One program that is "iffy" is the Voodoo chat client.  I've heard it can work in some builds of Linux using WINE...  but I think this VM solution just may be the ultimate workaround.   There are some concerns. I only have 128MB of physical ram on laptop which I'm thinking I'll upgrade to 384MB (max for that laptop)

I've tried both with a remote and a physical Windows 98 machine and (unless you use VirtualBox, but I'm not sure in this last one as I haven't tried VBox with 98 ) it hasn't worked, simply because W98 has no Terminal Services server compatible with seamlessrdp (or any rdp app). I had to put a Win2k server in my 133Mhz/48Mb RAM because 98 had no way to run RDP (which I'm gonna change to a homemade stripped down XP with nLite, as the machine didn't took 2k so well :/ ).

With 64Mb of virtual VMWare/QEmu/VBox RAM you can run a Win98 and *maybe* a Win2k server edition decently providing your laptop has enough Mhz/Ghz, you could try VBox with Win98 but for a sure shot, Win2k Server + any emulator will do for basic stuff such as IM programs, maybe a photoshop, IE 6, etc.

---

### Post by chrish670 on 2007-02-15
> **DARKGuy said:**
>  I've tried both with a remote and a physical Windows 98 machine and (unless you use VirtualBox, but I'm not sure in this last one as I haven't tried VBox with 98 ) it hasn't worked, simply because W98 has no Terminal Services server compatible with seamlessrdp (or any rdp app). I had to put a Win2k server in my 133Mhz/48Mb RAM because 98 had no way to run RDP (which I'm gonna change to a homemade stripped down XP with nLite, as the machine didn't took 2k so well :/ ).

With 64Mb of virtual VMWare/QEmu/VBox RAM you can run a Win98 and *maybe* a Win2k server edition decently providing your laptop has enough Mhz/Ghz, you could try VBox with Win98 but for a sure shot, Win2k Server + any emulator will do for basic stuff such as IM programs, maybe a photoshop, IE 6, etc.


Hmmm. I do have a OEM disk of XP Pro I was using on my desktop PC ... could try it, but I'll probably have to call Redmond for a new 56 digit product Key... Don't know what they'd say if I told them I was installing it in a Virtual box tho....  lol.

---

### Post by ffxr on 2007-02-15
clever stuff. ll be trying this next week.

i have 2 questions.

what technology allows you to log into the guest os remotely? is it terminal services? 
( i want to rip out any unmecessary bloat from xp before i install it, with nlite, and i dont wanna remove something i will need! )


also does anyone forsee any problems with using this guide for 64bit guests & hosts?

---

### Post by spockrock on 2007-02-15
> **DARKGuy said:**
> Whoah, that's a weird issue o_O... what version of XP are you running in the VM?


windows xp pro sp2 and vmware server 1.0.1 | 8/14/06 | Build 29996 :\

I am gonna do a reformat and re-install and see if that fixes the problem.

I did a reformat and re-install.....and same problem....I just don't get it......

---

### Post by Richardky on 2007-02-16
no sound  in Vmware isnt supported remotely ... was wondering if you get sound using the Qemu way ? or any other way... would be nice as i been looking for a way to use IM's yahoo's so i can use the conference feature without needing to dual boot just to do so ?

---

### Post by DARKGuy on 2007-02-16
> **Richardky said:**
> no sound  in Vmware isnt supported remotely ... was wondering if you get sound using the Qemu way ? or any other way... would be nice as i been looking for a way to use IM's yahoo's so i can use the conference feature without needing to dual boot just to do so ?

In QEmu it is supported, I use it :P

> **ffxr said:**
> clever stuff. ll be trying this next week.

i have 2 questions.

what technology allows you to log into the guest os remotely? is it terminal services? 
( i want to rip out any unmecessary bloat from xp before i install it, with nlite, and i dont wanna remove something i will need! )


also does anyone forsee any problems with using this guide for 64bit guests & hosts?

I dunno about 64 bits since I've never used a 64-bit system, but about the Windows question, yup, Terminal Services and RDP or something like that. Try running "services.msc" in Start -> Run and go to the properties page of Terminal Service, around you will find a Dependency tab or something similar which will tell you in what does that service depend on, just so you're double-careful and don't remove anything that Terminal Services might need.

> **spockrock said:**
> windows xp pro sp2 and vmware server 1.0.1 | 8/14/06 | Build 29996 :\

I am gonna do a reformat and re-install and see if that fixes the problem.

I did a reformat and re-install.....and same problem....I just don't get it......

I dunno really... :S you could do what I do: After installing XP and configuring, log out, then run the rdesktop script with c:\windows\system32\cmd.exe and a & at the end (so it stays on background), like "rdesktop -A -s "c:\rdp\rdp.exe c:\windows\system32\cmd.exe" &" . 

**At first run** it won't show anything, then you repeat the same command again and it will login back to WinXP and show you the cmd window. From there you can run other apps, try that and if it works, then I'll try to find a fix for it.

---

### Post by spockrock on 2007-02-17
> **DARKGuy said:**
> 
I dunno really... :S you could do what I do: After installing XP and configuring, log out, then run the rdesktop script with c:\windows\system32\cmd.exe and a & at the end (so it stays on background), like "rdesktop -A -s "c:\rdp\rdp.exe c:\windows\system32\cmd.exe" &" . 

**At first run** it won't show anything, then you repeat the same command again and it will login back to WinXP and show you the cmd window. From there you can run other apps, try that and if it works, then I'll try to find a fix for it.

yes that does work, I can launch apps in that manner, but I mean it would be alot easier if I could launch photoshop from gnome, use it.  Close it, and then next time I wanna use it, just click the launcher, instead of going back into vmware, and starting explorer and then loging off and then run photoshop again.

---

### Post by newpants2003 on 2007-02-17
nice post

---

### Post by Emanuel on 2007-02-17
Nice tutorial, but I keep getting the error:

Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Eventhough I did try the following:

sudo mknod /dev/kqemu c 250 0 
sudo chmod 666 /dev/kqemu

Any ideas? Thank you.

---

### Post by Richardky on 2007-02-17
> **Emanuel said:**
> Nice tutorial, but I keep getting the error:

Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Eventhough I did try the following:

sudo mknod /dev/kqemu c 250 0 
sudo chmod 666 /dev/kqemu

Any ideas? Thank you.

same error for me as well  :(

---

### Post by DARKGuy on 2007-02-17
> **Emanuel said:**
> Nice tutorial, but I keep getting the error:

Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Eventhough I did try the following:

sudo mknod /dev/kqemu c 250 0 
sudo chmod 666 /dev/kqemu

Any ideas? Thank you.

> **Richardky said:**
> same error for me as well  :(

Did you two try "sudo modprobe kqemu" ?

---

### Post by Emanuel on 2007-02-17
> **DARKGuy said:**
> Did you two try "sudo modprobe kqemu" ?

Not sure if that was it, but it is fixed now.

I restarted, enter all commands again and now no error anymore. Thank you.

---

### Post by wickstopher on 2007-02-17
I got up to step 4.  Windows XP, however, doesn't recognize my wireless usb device out of the box, and it doesn't recognize my optical drive for me to install the drivers, therefore I can't download seamlessrdp and get it running in my windows VM.  Any advice?

---

### Post by aktiwers on 2007-02-18
Wickstopher :
I dont think it should? If you are running it in Vmware, install Vmware Tools and try out the diffent connection settings. Really, your Vmware machine should just find your internet connection on Linux and use that.

Try it out, im sure you can get it to work. :)

---

### Post by lavs23 on 2007-02-20
I didn't know if I should post this in a new HOW TO or not but here's an idea I came up with to work with seamlessrdp and rdesktop easier, this guide will enable you to avoid having multiple user accounts to run different applications.

1.)  Install on your VM Machine a program launcher.  I chose PStart which you can get it here:
[http://www.pegtop.net/files/PStart209.exe]("http://www.pegtop.net/files/PStart209.exe")

2) Add programs into PStart that you want to run from Windows by right clicking in the empty area and selecting add File...

3) Once you have all your programs that you want to run start up Notepad in Windows and type

```
shutdown -l
```

and save this file as logoff.bat in your C: drive.

NOTE: The shutdown command can also restart or shutdown the virtual machine, the -l tag is for logoff.

4) Add the logoff.bat to your PStart menu.

5) Create a launcher in linux to launch PStart.
ex. rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Pegtop\PStart\PStart.exe" ipaddress -u username -p password

6) When ran it will bring up the same menu you saw in Windows, the next thing I did was change the settings in PStart to minimize to the taskbar when closed.  To do this in PStart goto Setup -> Settings... -> General -> Panel -> When closed minimize to taskbar.

There are some other settings that you can change in this menu, such as icon size.

Now you can close the PStart menu and it will be sent to your taskbar, when you are done using your Windows applications simply run the logoff.bat file and you'll be logged out and can start things back up without needed to mess with VMWare Server or QEmu.  Hope this helps out somebody, this is my first guide and just my fourth post so let me know what you think.

---

### Post by aktiwers on 2007-02-20
Great Guide and great Idea!
Thanks! :)

---

### Post by Miaowara on 2007-02-21
Hello, thanks for the great tutorial! I've a few questions though:

1. You have to be running qemu from this command: *qemu -localtime -m 384 -redir tcp:3389::3389 windows.img* in order to run the rdesktop commands, right?

2. Whenever I run commands to start programs (eg *rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\windows\system32\cmd.exe" IPADDRESS -u username -p password*) I just get another (larger) rdesktop and the program (such as cmd.exe in this case) doesn't start running (and the window can't be resized). Am I doing something wrong? In the initial image posted to this thread, IExplorer and MSN messenger don't seem to be constrained to the rdesktop window.

3. What IPADDRESS is needed? Since I'm just running an emulated Windows.img is *192.168.0.1* or *localhost* correct?

4. Is there anyway to increase the windows.img size after its created? I've only got 68mb left free!

Thanks again!

---

### Post by ss0007 on 2007-02-21
yep , i have the same issue , 
my USB webcam , USB storeage devices not detected in QMEMU , 
can someone help

---

### Post by aktiwers on 2007-02-21
> **Miaowara said:**
> Hello, thanks for the great tutorial! I've a few questions though:

1. You have to be running qemu from this command: *qemu -localtime -m 384 -redir tcp:3389::3389 windows.img* in order to run the rdesktop commands, right?

2. Whenever I run commands to start programs (eg *rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe c:\windows\system32\cmd.exe" IPADDRESS -u username -p password*) I just get another (larger) rdesktop and the program (such as cmd.exe in this case) doesn't start running (and the window can't be resized). Am I doing something wrong? In the initial image posted to this thread, IExplorer and MSN messenger don't seem to be constrained to the rdesktop window.

3. What IPADDRESS is needed? Since I'm just running an emulated Windows.img is *192.168.0.1* or *localhost* correct?

4. Is there anyway to increase the windows.img size after its created? I've only got 68mb left free!

Thanks again!

1) Yes and the other one if you are in VMware.
2)Did you remember to logout of Windows (being at the login screen)?
3)It should be the IP you find in windows. In Control Panel => Connections, there is one connection called VMware or something simulair. Right click, pick options and find the IP address.
4) I dont know.. but I dont think so, you will have to create a new virtual machine, or create a network between Windows and Linux, so you can use you Linux Harddrive space.

> yep , i have the same issue , 
my USB webcam , USB storeage devices not detected in QMEMU , 
can someone help

I use VMware, so I dont know. But in VMware you can share harddisc space with your Ubuntu install, so that you can use your harddisc space from Ubuntu. It works like when you are in a network with another PC, and can access its harddrive.

---

### Post by Miaowara on 2007-02-21
> **aktiwers said:**
> ...
2)Did you remember to logout of Windows (being at the login screen)?
3) It should be the IP you find in windows. In Control Panel => Connections, there is one connection called VMware or something simulair. Right click, pick options and find the IP address.
...


2) Even logged out, when I attempt to run a rdesktop command I get the whole desktop window again. Did I set something up incorrectly?
3)Looking in the Control Panel => Connections, all I see is "Local Area Network", there seems to be nothing there about VMware (though localhost seems to work).

I'm also wondering how to get sound functioning. When I start windows with

**qemu -soundhw all hda -localtime -m 384 -redir tcp:3389::3389 windows.img**

I keep getting:
```
oss: Could not initialize DAC
oss: Failed to open `/dev/dsp'
oss: Reason: No such file or directory
oss: Could not initialize DAC
oss: Failed to open `/dev/dsp'
oss: Reason: No such file or directory
audio: Failed to create voice `pcspk'
pcspk: Could not open voice

```

Some sort of problem with oss I gather. do I need some module loaded to get sound working?

Thanks for you help so far!:smile:

---

### Post by aktiwers on 2007-02-21
Oh! You are in Qemu.
Sorry I don't have much experience with Qemu, but in VMware the exact same problem  happends, when you forget to logout.

Why dont you install Vmware instead? I think you can open that Windows img from Vmware too (please correct me if im wrong!)

In Vmware its also easy to use sound in windows.. just share you soundcard with Ubuntu and bang! it works (atleast for me).

Also that Vmware connection will be easyer to find :)

Sorry I cant be of more help.
Good luck.

---

### Post by DARKGuy on 2007-02-21
Oh well, lots of people seem to have problems with the QEMU setup =/.... when I get some time I'll try to make another section for VMWare Server (it's a pain to run it here x_x).

On another note... ;)

[img]http://img480.imageshack.us/img480/5294/166mhzfn5.jpg[/img]

Yup, I took a spare computer I had around and installed XP in it, 1Gb HDD, HA!

---

### Post by Miaowara on 2007-02-22
Sorry Aktiwers, guess I should have specified that. :) Thanks for your help though! I'm not really sure how to set up Vmware so I'll look forward to seeing your howto [someday] DARK Guy! ;)

---

### Post by spockrock on 2007-02-24
lavs23

your pstart works great!!!

---

### Post by gabng on 2007-02-28
> **lavs23 said:**
> I didn't know if I should post this in a new HOW TO or not but here's an idea I came up with to work with seamlessrdp and rdesktop easier, this guide will enable you to avoid having multiple user accounts to run different applications.

1.)  Install on your VM Machine a program launcher.  I chose PStart which you can get it here:
[http://www.pegtop.net/files/PStart209.exe]("http://www.pegtop.net/files/PStart209.exe")

2) Add programs into PStart that you want to run from Windows by right clicking in the empty area and selecting add File...

3) Once you have all your programs that you want to run start up Notepad in Windows and type

```
shutdown -l
```

and save this file as logoff.bat in your C: drive.

NOTE: The shutdown command can also restart or shutdown the virtual machine, the -l tag is for logoff.

4) Add the logoff.bat to your PStart menu.

5) Create a launcher in linux to launch PStart.
ex. rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Pegtop\PStart\PStart.exe" ipaddress -u username -p password

6) When ran it will bring up the same menu you saw in Windows, the next thing I did was change the settings in PStart to minimize to the taskbar when closed.  To do this in PStart goto Setup -> Settings... -> General -> Panel -> When closed minimize to taskbar.

There are some other settings that you can change in this menu, such as icon size.

Now you can close the PStart menu and it will be sent to your taskbar, when you are done using your Windows applications simply run the logoff.bat file and you'll be logged out and can start things back up without needed to mess with VMWare Server or QEmu.  Hope this helps out somebody, this is my first guide and just my fourth post so let me know what you think.

Excellent tip!  Works flawlessly!  Thanks!

---

### Post by TheShadow99 on 2007-02-28
Hello,

I'm trying to use this to run certain windows apps on client machines that have issues being used under linux by running them from a win 2k3 file server... However I am having a few issues. First I can't seem to login more than 1 user at a time. Some of the client systems need to be connected for long stretches of time and other users may need to connect to the same system during that time.

Also has anyone found a way to create a frontend for this that would allow you to choose an app or more than one at a time? I can put a launcher in place that runs the command, but since each is it's own remote connection this doesn't allow you to run more than one app at a time. cmd.exe or pstat let you run more than one app, but none are 'visual' in their app selection...

---

### Post by superami on 2007-03-02
I have some problems with the rdesktop.  I'm trying to use rdesktop to login to my corporate computer to access individual programs.  I have successfully done this with a standard windows XP, but with the corporate one it always asks me for my password in a new window and then logs me in to a standard full remote desktop.  Does anyone have any ideas?

---

### Post by m.musashi on 2007-03-04
This sounds very cool. I'm curious though. I have XP running in vmware. Is this an alternative to that? In other words, can I uninstall vmware and just do this? Can this method also work for installing other OSs? I also have a 64bit edgy running via vmware. Finally, does this just result in one app running rather than the whole OS? What happens if you need to run two apps that interact? For example, clonedvd needs anydvd to work.

Thanks.

---

### Post by Kratos on 2007-03-04
Hrm, there seems to be a kink in this idea, somewhere. When I try to enable Remote Access in Windows, the entire section is missing.

See attached screen shot for an example. 

I think this could be explained by the fact that I'm using Windows XP Home Edition, instead of Pro. :/ If there's any way of being able to do this in Home Edition, I'd be set.

EDIT: Above is confirmed. I cannot use Remote Desktop in XP Home.

Are there any third-party apps that would do the same thing?

---

### Post by customs on 2007-03-05
> **Kratos said:**
> Hrm, there seems to be a kink in this idea, somewhere. When I try to enable Remote Access in Windows, the entire section is missing.

See attached screen shot for an example. 

I think this could be explained by the fact that I'm using Windows XP Home Edition, instead of Pro. :/ If there's any way of being able to do this in Home Edition, I'd be set.

EDIT: Above is confirmed. I cannot use Remote Desktop in XP Home.

Are there any third-party apps that would do the same thing?

You can convert XP Home to Professional in a few steps:

1. Start regedit.exe from the command prompt.
2. Open HKEY_LOCAL_MACHINE then SYSTEM and then ControlSet with the highest value (in my registry it was ControlSet004)
3. Then Control, ProductOptions. In the ProductOptions section click on ProductSuite and remove it completely.
4. Add new DWORD string with the name Brand and zero value
5. Close regedit and reboot your computer. When rebooting click F8 to access windows startup menu and choose "The last successful configuration" (I can't exactly remember, because I have a Russian version of Windows).
That's all. Now you have the Professional version.

Before these steps I recommend to backup a registry by some app or manually.


If you like to have the ability to use your physical windows box while working with a remote desktop you can add a new user (with admin rights) and install this patch: [http://sala.pri.ee/?page_id=11]("http://sala.pri.ee/?page_id=11")

Now your wife can check her email while you're working with a remote desktop :)

---

### Post by Kratos on 2007-03-05
> **customs said:**
> You can convert XP Home to Professional in a few steps:

1. Start regedit.exe from the command prompt.
2. Open HKEY_LOCAL_MACHINE then SYSTEM and then ControlSet with the highest value (in my registry it was ControlSet004)
3. Then Control, ProductOptions. In the ProductOptions section click on ProductSuite and remove it completely.
4. Add new DWORD string with the name Brand and zero value
5. Close regedit and reboot your computer. When rebooting click F8 to access windows startup menu and choose "The last successful configuration" (I can't exactly remember, because I have a Russian version of Windows).
That's all. Now you have the Professional version.

Before these steps I recommend to backup a registry by some app or manually.


If you like to have the ability to use your physical windows box while working with a remote desktop you can add a new user (with admin rights) and install this patch: [http://sala.pri.ee/?page_id=11]("http://sala.pri.ee/?page_id=11")

Now your wife can check her email while you're working with a remote desktop :)

Your advice managed to solve one problem. But, it seemingly created a new one. So, the System Properties Dialog reports that I'm now using Windows XP Pro. But, now, then entire Remote tab of said dialog, is gone.

EDIT: I think the method you suggested was merely a means of tricking Windows into thinking it was XP Pro, and didn't really do anything to add the functionality it lacked as XP Home Edition.

---

### Post by RanShak on 2007-03-10
Everything was going great until I got to the Testing step. I run the command and I'll get either Connection reset by peer or Connection refused. Any ideas?

---

### Post by newguy28 on 2007-03-10
hi, im new to linux, when i type sudo apt-get install qemu build-essential linux-headers-`uname -r` on the terminal i got answer that qemu package is not found. is there something missing? thanks

---

### Post by ahmatti on 2007-03-12
GREAT howto! Seamlessrdp works perfectly with qemu with kqemu in Feisty! 

Ok I had to downgrade back to edgy because of some other problems with Edgy and I am noe giving Virtualbox a try. It is a lot faster than qemu with kqemu, but I haven't got seamlessrdp or even a normal remote desktop working.

Does anyone know how to do this with virtualbox?

---

### Post by bikuta on 2007-03-12
> **newguy28 said:**
> hi, im new to linux, when i type sudo apt-get install qemu build-essential linux-headers-`uname -r` on the terminal i got answer that qemu package is not found. is there something missing? thanks

I get the same problem too, it can't find the qemu package.
I've just done a clean install of Dapper and upgraded to Edgy.

What am I supposed to do so that it finds the package?

---

### Post by ahmatti on 2007-03-13
> **bikuta said:**
> I get the same problem too, it can't find the qemu package.
I've just done a clean install of Dapper and upgraded to Edgy.

What am I supposed to do so that it finds the package?

Try enabling multiverse and universe (I am not sure which one has qemu & kqemu) repos. You can do this e.g with synaptic from the menu "setting->repositories" and then just tick the repositories you wan't to use. 
 
I also find qemuctl very useful. You can use it to suspend the machine and change the cdrom from iso to physical device or another iso when the VM is running etc. :)  So instead of running "qemu -options vm.img" you run "qemuctl -options vm.img"

---

### Post by bikuta on 2007-03-13
> **ahmatti said:**
> Try enabling multiverse and universe (I am not sure which one has qemu & kqemu) repos. You can do this e.g with synaptic from the menu "setting->repositories" and then just tick the repositories you wan't to use. 


Yep thanks. I had to enable universe in my sources, now all my other installs work too!

---

### Post by frodonet on 2007-03-14
I have a problem running step 5 with this command

sudo mount /dev/cdrom 

it says no medium found. Can help me???

---

### Post by arunsub on 2007-03-14
I have a dual boot system. I installed Windows and remote desktop as per the instructions here, in my Ubuntu box. I came to this point where the instruction said **Extract it to C:\seamlessrdp**. Does C: drive point to the virtual C drive or the physical C drive of the dual boot system?  If it's virtual, how do I extract it to virtual C drive? If it's physical, then my C drive partition is NTFS and non writable. How do I make it work? 
Sorry if the question is silly.

---

### Post by aktiwers on 2007-03-15
I don't get your question?
Are you trying to connect to the windows install you have on the same machine with dualboot? You cant do that. Windows need to be loaded and at the login screen.

And by the way, you can read/write to NTFS. Have a look here for that:
[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

Again, try to explain the problem in more detail and I might be able to help.
Cheers!

---

### Post by arunsub on 2007-03-15
I wrote the dual boot just to describe my machine. I'm not trying to connect to dual boot Windows installation. I'm following the instruction here to install the WIndows virtual machine using QEMU. My question is regarding STEP 4:

[B]Step 4: Installing the required software in the server machine or guest OS

Download [http://www.cendio.se/files/thinlinc/...eamlessrdp.zip](http://www.cendio.se/files/thinlinc/...eamlessrdp.zip).

Extract it to C:\seamlessrdp or something similar, a short path without spaces or long names preferably. After it's extracted, just log out the VM (or the user session in your physical box).
[/B]

It says extract it to C:\seamlessrdp. I want to know which C drive? How do I extract it to C drive?

---

### Post by ahmatti on 2007-03-16
> **arunsub said:**
> 
It says extract it to C:\seamlessrdp. I want to know which C drive? How do I extract it to C drive?

The c: drive of your qemu virtualbox. There is built in zip extractor in WinXP. Just right click the downloaded file in windows and select "Extract all"

---

### Post by arunsub on 2007-03-16
Ok. That cleared my doubt. The internet conx in my windows virtual box didn't work. I have to check that and then download this. I'll try it when I go home and see if it works. Thanks for the help.

---

### Post by Emanuel on 2007-03-18
Hi,

Eventhough I think it's great software and a great tutorial,

I still think it's not optimal yet. If I run window programs then it is a bit slow.. it is too slow to completely stop using windows. I run it now with 1024 mb memory, but not fast enough.

I was wondering, are there any methods to speed it up? Free or paid solutions.

Greetings.

---

### Post by azteech on 2007-03-18
Okay,
I will admit that I still have a dual boot system, M$ Win XP Pro and Ubuntu Edgy Eft (6.10). Main reason I don't give up window$ entirely is my banking info can't be accessed from Ubuntu, using FF (because of the bank), and the annual tax prep software we all have to use.

I would love to free up hd space, make Ubuntu my sole OS, and only run window$ to do taxes and download banking info ....  I am looking to follow this help guide to get window$ running under Ubuntu. 

I currently run on an older HP computer, 850MHz, 512MB ram, 128MB Nvida card, dual hd's totaling 200GB combined.  

The three questions I have are (and for which I find no answer to in this thread):

1. For those who have successfully implemented this configuration, what would you recommend for CPU speed and memory config to make this happen? 

2. Would it make more sense to not implement this solution until I upgrade the speed and memory of the computer?

3. Given my current configuration, will I be able to implement the how-to, and run the software (successfully), all be it will run slower than what I am use to when running XP in native mode?

Any advise/input is greatly appreciated in advance.

---

### Post by ahmatti on 2007-03-18
> **Emanuel said:**
> Hi,

Eventhough I think it's great software and a great tutorial,

I still think it's not optimal yet. If I run window programs then it is a bit slow.. it is too slow to completely stop using windows. I run it now with 1024 mb memory, but not fast enough.

I was wondering, are there any methods to speed it up? Free or paid solutions.

Greetings.

Give Virtualbox a try, It is much faster for me. I haven't get seamlessrdp working with it yet though.

---

### Post by arunsub on 2007-03-18
I got everything working, but the problem now is, I can't access the volume control through All Program -> Accessories - > Entertainment -> Volume Control. I get "there's no active mixer devices available. To install mixer devices, go to control panel, click printer and other hardware, and then click add hardware." error. I want to get my mic to work. The other beep sounds work.

---

### Post by statictonic on 2007-03-19
Has anyone been able to get rdesktop to work with 24 bit color?  As far as I know WinXP Pro supports up to 24 bit color for RDP, but the vmware drivers have it only shown as able to run 16 bit or 32 bit color, not sure if this could be causing this issue or not.  I haven't been able to get it to go over 16 bit color.  Also I'm having a problem in photoshop where the top toolbar right below the File menu doesn't work at all, anyone else have this issue?

I had a friend put together a PHP script ran by a VB app, so you can start the virtual machine rdesktop connection, nothing will appear on ubuntu.  Then I wrote a shell script you can put into /bin so all you have to do to launch a windows app would be to type windows photoshop for example in linux.  I also wrote it so it can take a single exe from the linux partition and automatically copy it to and run it on the windows computer.  In otherwords you could type windowsinstall /home/user/windowsfile.exe(you can also set gnome to do this automatically for exe's or any file for that matter) and it's run it or pull up an installer if needed, this currently does not work if it has any other files it needs though.

I'll post info on this up here later with my scripts, I gotta make them a bit more trouble free first though.

---

### Post by raymond3 on 2007-03-22
So I have this running using VM and and I can use Outlook except when I create a new message it pops up with a black box instead of the compose window.  Can someone try to use a program that opens a new window (or even outlook) and see if it does the same thing?

---

### Post by yj09 on 2007-03-22
I try to install windows in physical drive but receive permission error. can anybody help  
me to solve this problem.

---

### Post by josir on 2007-03-24
Hi folks, on the first line I got an error:

josir@Linux02:~$ sudo apt-get install qemu build-essential linux-headers-`uname -r`
Password:
Reading state information... Ready
E: Impossible to find package linux-headers-2.6.15-28-amd64-generic

As I understood, I don't have this package on my source.list repositories. I also tried:

josir@Linux02:~$ sudo apt-get install  linux-headers
Lendo Lista de Pacotes... Pronto
Construindo Árvore de Dependências       
Reading state information... Pronto 
O pacote linux-headers é um pacote virtual provido por:
  linux-headers-2.6.17-11-server 2.6.17.1-11.35
  linux-headers-2.6.17-11-generic 2.6.17.1-11.35
  linux-headers-2.6.17-11 2.6.17.1-11.35
  linux-headers-2.6.17-10-server 2.6.17.1-10.34
  linux-headers-2.6.17-10-generic 2.6.17.1-10.34
  linux-headers-2.6.17-10 2.6.17.1-10.34

In fact, I've already have kernel 2.6.17 installed but as far as I know, this is not a 64bits kernel. That's why I am using 2.6.15 kernel.

Does somebody have any tip?

Josir

---

### Post by UbunduNoob on 2007-04-02
greetings.  I followed the instructions on this page and all was going well.

I hit a snag when i shut down the running windows before performing step 3a.

now I can't seem to launch windows.
----------------------------------------------------------------
adonis@adonis-desktop:~$ sudo modprobe kqemu
Password:
adonis@adonis-desktop:~$ sudo mknod /dev/kqemu c 250 0
mknod: `/dev/kqemu': File exists
adonis@adonis-desktop:~$ sudo chmod 666 /dev/kqemu
adonis@adonis-desktop:~$ qemu -localtime -m 384 -redir tcp:3389::3389 windows.img
qemu: could not open hard disk image 'windows.img'
----------------------------------------------------------------

any help would be appreciated.
Thank you

---

### Post by devastater on 2007-04-03
Nice howto. I manage to follow all the steps and get it to run. But the program run rather slowly and I receive this message.
Could not open '/dev/kqemu' - QEMU acceleration layer not activated

Can someone explain how to activate QEMU acceleration?
Thanks

---

### Post by DARKGuy on 2007-04-03
It's explained in the HowTo, read it with more detail and you'll find how :)

---

### Post by spankymasterc on 2007-04-03
I need help im Using Vmware Workstation and i did every step as told but when i run the command rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\path\path.exe (using what ever path)" 192.168.208.128 -u user name -p password

All it does is log me in my virtual machine and give me a full screen of my virtual machine any help would be greatly appreciated....

---

### Post by AusIV4 on 2007-04-03
I just got this working using a physical windows machine, and I've got a few issues.

First is sound. I don't have it. When rdesktop starts up I get a line that says "/dev/dsp: Device or resource busy". Then I don't get sound from any applications.

I'm also having issues with iTunes. I had intended to pull it up and see what kind of response I got from it, but it doesn't even open. 

Lastly, I tried running a program that minimizes to the system tray. Once I minimized it, there was no way to get it back. Is there any way to load the windows taskbar? It would be kinda cool to have that at the top of my screen while I have the Kicker at the bottom.

---

### Post by Aetherius on 2007-04-18
Hey, got this running perfectly first go using qemu, but my image was too small so i reinstalled windows on a new bigger image. and now when i rdesktop into it I only get a HUGE (bigger than the screen) desktop,

 i load qemu with ```
qemu -cdrom /dev/cdrom -localtime -m 384 -redir tcp:3389::3389 winxp.img &

```

and I rdesktop with```
rdesktop -rsound -A -s "C:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" localhost:3389 -u remote -p remote

```

Any ideas on whats gone wrong?

EDIT: nevermind, it's suddenly decided to work perfectly

---

### Post by cumanzor on 2007-04-22
I have a question. I managed to get it working with VirtualBox. I installed Windows Server 2003 inside the virtual machine and it runs great in there. But once I start an application with rdesktop it is so slugish. Feels like the screen refresh is slow, you can actually see while some windows are being draw.

Any ideas? I thought of the virtual network speed (real machine to virtual machine connection)....

---

### Post by DARKGuy on 2007-04-22
Hm, I never got around to make it work in VirtualBox... it always showed me a rdesktop window but no like it should (without explorer.exe and just showing the windows) so I dunno about that :(

Anyways, I got some time now and I'm under Linux. Considering VMWare Server is free now, I'll remove the qemu HowTo since it looks like it's been causing lots of problems with lots of people and I'm gonna replace it with a VMWare HowTo. That'll be better :)

Also, there's no need to compile rdesktop now if you're using Feisty, so that's one step less! ^^

---

### Post by cumanzor on 2007-04-23
> **DARKGuy said:**
> Hm, I never got around to make it work in VirtualBox... it always showed me a rdesktop window but no like it should (without explorer.exe and just showing the windows) so I dunno about that :(

Anyways, I got some time now and I'm under Linux. Considering VMWare Server is free now, I'll remove the qemu HowTo since it looks like it's been causing lots of problems with lots of people and I'm gonna replace it with a VMWare HowTo. That'll be better :)

Also, there's no need to compile rdesktop now if you're using Feisty, so that's one step less! ^^

it works for me, a single window... even if I'm already logged in in the VM (try logging out, I read that solves the problem). My issue is the it's so slow in the rdp...

---

### Post by DARKGuy on 2007-04-25
> **cumanzor said:**
> it works for me, a single window... even if I'm already logged in in the VM (try logging out, I read that solves the problem). My issue is the it's so slow in the rdp...

Do you have the kqemu module loaded? that could help. Also, take note that your system specs must be high enough to be able to stand a VM, Linux, and the apps running on both, counting the emulation load over Linux & the VM too.

---

### Post by zhinker on 2007-04-25
Does this stuff allow you to use hardware that would otherwise be incompatible with Ubuntu, like some TV tuners perhaps?

---

### Post by kevmartin on 2007-04-25
> **zhinker said:**
> Does this stuff allow you to use hardware that would otherwise be incompatible with Ubuntu, like some TV tuners perhaps?

As I understand it, none of the virtualization options will allow you to do that.

---

### Post by st33med on 2007-04-25
Can I have it run my physical partition? I have windows already installed on my dual-boot system. I just don't want to waste space.

---

### Post by pmgeahan on 2007-04-27
I've been trying to download seamlessrdp from Cendio, but the .zip link keeps returning a 404.

Does anyone have a link to another place where the .zip is hosted?

---

### Post by CyBuzz on 2007-04-28
> **pmgeahan said:**
> I've been trying to download seamlessrdp from Cendio, but the .zip link keeps returning a 404.

Does anyone have a link to another place where the .zip is hosted?

DItto, I finally get around to trying this out and bam, this happens](*,)

---

### Post by pmgeahan on 2007-04-28
> **CyBuzz said:**
> DItto, I finally get around to trying this out and bam, this happens](*,)

Yeah, that was kind of my feeling as well.  However, I managed to find another link and got the whole shebang working:

[http://howtoforums.net/downloads/seamlessrdp.zip](http://howtoforums.net/downloads/seamlessrdp.zip)

I've got some things I want to try to figure out how to tweak; specifically, when I start a new application, rdesktop/seamlessrdp briefly takes over my whole screen until the app launches, and then returns control back to me.  Brief, but annoying.

---

### Post by HunterK on 2007-04-28
If I read this right, is this basically running apps from the remote machine on Linux without having to logon to the remote machine through rdesktop?  Do you still encounter any lag, etc if the machine is not on your network?  What about video acceleration? You can play games or anything can you?

---

### Post by LoKR on 2007-04-29
Hey, here is a tip that I found useful:
If you want to print to screen ONLY the windows taskbar (try to run rdesktop -A ... "c:\windows\explorer.exe" and you'll see what I mean)
Log in the user you'll use to remote desktop in your virtual machine of physical machine,
open regedit then 
HKey_Current_User \ Software\ Microsoft \Windows \ Current Version \ Policies \ Explorer
Create a new DWORD value that you'll call NoDesktop and then put the value to 1 
log off and now remote desktop c:\windows\explorer.exe and you'll see the parallel like effect ;-)

P.S > it's cool, I've got XGL and the windows from windows XP have the fancy effects :D

---

### Post by jmvidalvia on 2007-07-05
Hello!
Everything seems to work, but I amb getting this messages in my console:
```
NOT IMPLEMENTED: SeamlessRDP SETICON1
Got "BadMatch" when trying to restack windows.
This is most likely caused by a broken window manager (commonly KWin).

```
Does anybody know how to solve this?
Thanks!

---

### Post by sheepdogj15 on 2007-08-04
> **AusIV4 said:**
> I just got this working using a physical windows machine, and I've got a few issues.

First is sound. I don't have it. When rdesktop starts up I get a line that says "/dev/dsp: Device or resource busy". Then I don't get sound from any applications.


I have the same problem. It seems that rdesktop uses OSS for sound, which is an old and obsolete audio backend which doesn't support software mixing. i have the same problem. it means that something else is using the sound card, so that rdesktop can't. (probably artsd, or bob forbid, your virtual machine itself.)

i've been playing with it, trying to get sound to work without killing other apps. (i *want* kde sounds and the like.) the closest i get is to use aoss. e.g.:

> aoss rdesktop -rsound -u [user] -p [pass] -A -s "C:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Winamp\winamp.exe" localhost

what aoss does is trick applications into using ALSA (newer, better sound backend that does support sound mixing) and thinking they are actually using OSS. 


problem i have with this is that some apps, the sound is distorted. like it's playing 44.1kHz at 48KHz or something. **has anyone else tried to figure it out????**

---

### Post by LordMau on 2007-08-20
I'm following the feisty howto using vmware.

The instructions state i need host-only networking. That said I am able to successfully run skype for windows, in7 etc ok. But those apps are unable to see the net though.

So what should I do to enable internet access to those seamless apps while still maintaining host-only networking within vmware? Or is that not possible? Is so how should I proceed?

---

### Post by fjgaude on 2007-08-20
> **LordMau said:**
> I'm following the feisty howto using vmware.

The instructions state i need host-only networking. That said I am able to successfully run skype for windows, in7 etc ok. But those apps are unable to see the net though.

So what should I do to enable internet access to those seamless apps while still maintaining host-only networking within vmware? Or is that not possible? Is so how should I proceed?

Use NAT as your networking mode... if you have to get on the Internet that's one way.

Is there a reason you don't wish to get on the net?

frank

---

### Post by LordMau on 2007-08-21
> **fjgaude said:**
> Use NAT as your networking mode... if you have to get on the Internet that's one way.

Is there a reason you don't wish to get on the net?

frank

Not at all. Actually I really do want to access the net as the reason I'm studying this is to use Skype with Video under ubuntu.

I was just taken aback by how explicit the notice was to use host-only networking in the guide. I just don't know any better hence my apprehension.

On that note though I'm able to run  skype, I don't have sound in or out yet, as well as video. Still studying what to do for now.

---

### Post by Roque on 2007-08-21
Hi.

Today I installed VirtualBox with feisty as host and XP as guest. It runs fine, of course. But I already have a dualboot system with XP installed and updated continuously since two years. I'd like to use this one as a guest, but apparently I am forced to install XP from scratch since the guest must be virtualized in a VDI volume. 

Is there a way to do what I want? If so XP could be accessible both ways: the usual nonvirtual one and from inside the VM. It would also save lots of space (otherwise XP would be duplicated on disk) and a lot of work (updating, downloading all software/patches, recreating mail accounts, etc.)

---

