---
title: "[SOLVED] Daemon Tools Lite."
date: 2008-07-07
forum: General Help
---

### Post by Dyffo on 2008-07-07
I am now 100% UBUNTU ( Hardy Heron ) when I had Windows I used software (downloaded) called DAEMON TOOLS LITE this was used to mount and prepare a virtual CD drive -  this enabled me to play .bin  .cue .rar and .dat files via my computer media player. The files were mostly interactive DVD Games which I could not convert to use on DVD players - they needed CPU and so on.
All this rambling is to ask - has anyone any idea of equivalent software for UBUNTU. that will perform this function. I have contacted Daemon software to see if they have a Linux version - NO response !! :confused:

---

### Post by bodhi.zazen on 2008-07-07
There are a few tricks to this on linux.

Linux mounts .iso directly.

```
sudo mkdir /media/iso
```

Now mount your .iso :

```
sudo mount -o loop -t iso9660 /path/to/filename.iso
```

If you want a gui, look at gmountiso (sudo apt-get install gmountiso)

---

### Post by hawthornso23 on 2009-08-26
sudo mount <file.iso> <mountpoint> -t iso9660 -o loop


will not work on isos made from securom copy protected discs and the like. However I have discovered that you can still get access to these iso files in ubuntu via the following trick. You need a windows computer with demon tools lite installed on your local network to make this trick work. You also need to have both samba and smbclient installed. 

Step 1. Put the iso file on the windows machine.

Step 2. Create a virtual disc drive in demon tools lite on windows. Mount the iso file.

Step 3. In windows explorer share the virtual disk drive across the local network, and give it a share name. In my case 'demondrive'. 

Step 4. Find the IP number of the windows machine. In my case 10.1.1.6 

Step 5.  Prepare a mount point on the ubuntu machine. In my case
sudo mkdir /media/iso


Step 6. Mount 
sudo mount //10.1.1.6/demondrive  /media/iso -t smbfs 


I was  astonished that this worked as well as it did. If you make the mountpoint 
into a drive in wine, and set its type as cdrom in advanced, you can even install software 
directly into wine from it. Effectively this trick turns the networked windows machine 
into a rather efficient virtual external cdrom drive for ubuntu.

When you are finished don't forget to

Step 7. Unmount
sudo umount /media/iso


Enjoy.

---

### Post by DeMus on 2009-08-26
> **Dyffo said:**
> I am now 100% UBUNTU ( Hardy Heron ) when I had Windows I used software (downloaded) called DAEMON TOOLS LITE this was used to mount and prepare a virtual CD drive -  this enabled me to play .bin  .cue .rar and .dat files via my computer media player. The files were mostly interactive DVD Games which I could not convert to use on DVD players - they needed CPU and so on.
All this rambling is to ask - has anyone any idea of equivalent software for UBUNTU. that will perform this function. I have contacted Daemon software to see if they have a Linux version - NO response !! :confused:

It's even simpler than what you wrote in your last post. Just do this and be amazed:

Mount and unmount Iso-files

Using Nautilus Scripts
First we have to download two scripts, one to mount an ISO file and one to un-mount an ISO file.
The two scripts can be downloaded here:
Script to mount a file: [here]("http://www.debianadmin.com/images/iso/mount.sh")
Script to un-mount a file: [here]("http://www.debianadmin.com/images/iso/unmount.sh")
Download them to the normal folder you always use to download files.
Once you have these two scripts you need to change the permissions using the following commands
Open a terminal.  To do this click Applications > Accessories > Terminal
Type
```
cd name/of/downloadfolder (e.g. Downloads)
```
```
sudo chmod +x mount.sh
sudo chmod +x unmount.sh
```
Now you need to move the 2 nautilus scripts to the right folder:
```
sudo mv mount.sh ~/.gnome2/nautilus-scripts/
sudo mv unmount.sh ~/.gnome2/nautilus-scripts/
```
This will place the 2 files in a hidden folder in your user area.
Now when you right-click on a file you will see an extra line in the menu which is called Scripts. Follow the little arrow to the right and choose either mount.sh or unmount.sh.

---

### Post by Dyffo on 2009-08-26
:KS Hi Guys - Very pleased to hear that you are sorted. This is an ancient POST.
I have moved on now to Linux Mint - this really is worth a look. 
this is UBUNTU based, but has many advantages.:P

---

### Post by bodhi.zazen on 2009-08-26
There are gui tolls for this now :

[http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html](http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html)

---

### Post by xieqiao on 2011-08-20
> **DeMus said:**
> It's even simpler than what you wrote in your last post. Just do this and be amazed:  .... you right-click on a file you will see an extra line in the menu which is called Scripts. Follow the little arrow to the right and choose either mount.sh or unmount.sh.

Thank you. But I tried to open an NRG file with right-click, it says it can't open it.  I have installed Furius ISO,  AcetoneISO,  MountManager, Gmount-iso and  cdemu. But none of them worked. Only Furius ISO Mount Tool could  seemingly mount an NRG image, but there is only blank related to the  image folder within the Nautilus file manager.  

 I even tried the following command lines.  But I'm really not good at  command lines in a terminal.  I read the following instructions, and  experimented, but to no fruition.  Are there other simpler means to  mount an NRG image?  

[https://help.ubuntu.com/community/ManageDiscImages](https://help.ubuntu.com/community/ManageDiscImages)

To Mount

sudo mkdir /media/example 

sudo mount -o loop,offset=307200 /path/to/example.nrg /media/example

---

### Post by 3rdalbum on 2011-08-20
"NRG" is just the same as "ISO", isn't it? It was when I last tried. Maybe just try renaming the file so it ends in .iso rather than .nrg.

---

### Post by xieqiao on 2011-08-20
> **3rdalbum said:**
> "NRG" is just the same as "ISO", isn't it? It was when I last tried. Maybe just try renaming the file so it ends in .iso rather than .nrg.

I have renamed it with *.iso, but the file still could not be opened.

---

