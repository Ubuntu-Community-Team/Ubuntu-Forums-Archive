---
title: "mounting bin/cue files with cdemu"
date: 2008-02-12
forum: General Help
---

### Post by Cha1n5aW on 2008-02-12
I've read a number of threads regarding usage of cdemu & have done everything everyone suggested.  I suppose I should start from the beginning.  I downloaded all the newest cdemu packages from the cdemu sourceforge site.   All the packages installed without any problems.  I then followed the instructions at [http://ubuntuforums.org/showthread.php?t=276743]("http://ubuntuforums.org/showthread.php?t=276743")  
made the nautilus scripts and everything.  When I try to mount the .cue file using the nautilus script I get the following error...
"You can not mount any more images."
I of course do not have any images mounted.  So, I try to mount the image from terminal prompt using the following command...
```
cdemu load freespace2_1.cue
```
and get the following error
```
ERROR: Failed to connect to CDEmu daemon: org.freedesktop.DBus.Error.ServiceUnknown: The name net.sf.cdemu.CDEMUD_Daemon was not provided by any .service files
ERROR: Failed to connect to daemon!

```
I've done as much searching and forum research and everything else I can possibly think of, if anyone knows what I've done wrong, any help or insight would be greatly appreciated.  I'm at the point where the time I've spent messing around with cdemu, I could have just converted the .bin images to .iso formats and just did the good ol' mount loop and would likely be playing freespace2 by now.

Thanks
- Shawn

---

### Post by Christmas on 2008-02-12
I never used CDEmu, but here's what I do. Whenever I have an image which is not in ISO format, I convert it with either 'nrg2iso' (for Nero NRG images) or 'iat', which supports a lot of formats. Then, mount it with:
```
sudo mount -o loop your_image.iso /media/cdrom0
```
You have to be root to unmount it. There is always some package I heard of which allows you to mount it as normal user, but can't recall the name now.

---

### Post by Cha1n5aW on 2008-02-14
I gave up on the whole cdemu thing, big waste of time IMO.  The easiest way I found of doing it is to get a little program called Binchunker (sudo apt-get install bchunk), and a little gnome app called Gmount-iso (graphical frontend to mounting images).  Binchunker converts .bin/cue files to .iso quickly and then I just open gmount-iso, and click the image and mount it.. super easy, and very little command line stuff involved.  Gmount-iso also graphically unmounts the iso file as well.  Thanks for lettin' me in on the other  conversion programs, I'll definitely have to install em', as I think binchunker only converts .bin/cue files.

Thanks
- Shawn

---

### Post by Shadowmeph on 2008-02-17
> **Cha1n5aW said:**
> I gave up on the whole cdemu thing, big waste of time IMO.  The easiest way I found of doing it is to get a little program called Binchunker (sudo apt-get install bchunk), and a little gnome app called Gmount-iso (graphical frontend to mounting images).  Binchunker converts .bin/cue files to .iso quickly and then I just open gmount-iso, and click the image and mount it.. super easy, and very little command line stuff involved.  Gmount-iso also graphically unmounts the iso file as well.  Thanks for lettin' me in on the other  conversion programs, I'll definitely have to install em', as I think binchunker only converts .bin/cue files.

Thanks
- Shawn

How do I load Binchunker?

---

### Post by Ferrat on 2008-02-17
cdemu works great for me but I had the problem with the deamon not getting started as it should, this is how I solved it 

it's the module for vhba that gets jammed for some reason 

try 

```

$ sudo /etc/init.d/cdemu-daemon restart

```

most likely you will get 
>      * Stopping CDEmu daemon                                [ OK ]                                                          
     * Killing daemon...                                   [[COLOR="Red"]fail[/COLOR]]                                  
     * Removing kernel module (vhba)...                   [[COLOR="Red"]fail[/COLOR]]

So just run 

```

sudo modprobe vhba

```

and then try 


```

$ sudo /etc/init.d/cdemu-daemon restart

```

again and you should get a restart of cdemu

---

### Post by Cha1n5aW on 2008-02-17
I believe that was the problem I was having as well, iirc the error messages I encountered when attempting to use cdemu likely indicated that the daemon wasn't loading.  I've since reinstalled ubuntu for other reasons & this time around I didn't even install cdemu, I just installed all the various conversion programs (binchunker, nrg2iso,  iat) & Gmount-iso.  Thanks for the fix tho, if I decide to give it another try, I'm sure your suggestion will be valuable.

- Shawn

---

### Post by Cha1n5aW on 2008-02-17
> **Shadowmeph said:**
> How do I load Binchunker?

I just installed the package using...
```
 sudo apt-get install bchunk 
```
I'm sure you could likely install the package in synaptics package manager, but terminal command is quicker than searching the repository.

once its installed just open a terminal run it like this...
```
 sudo bchunk -v ~/filename.bin ~/filename.cue ~/outputfile.iso 
```

enjoy

- Shawn

---

### Post by KingWilliam on 2008-02-21
I have the same problem with CDemu. What I tried is compiling all packages by myself. The problem is that I (and you probably too because we have the same error) can't find cdemu-daemon in /etc/init.d . So you can't start neither restart it. Thats why when you try using CDemu it says it cant find the daemon. I give up with CDemu to. Daemon tools for Linux just sounded too beautiful...

---

