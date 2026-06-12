---
title: "firestorm on ubuntu"
date: 2012-10-21
forum: General Help
---

### Post by hernan989 on 2012-10-21
Hi, sorry i'm very new with this, i just installed ubuntu and i wanna run firestorm (viewer for second life). I download it, and it says it doesnt need to be installed, so i just run the "firestorm" file.. but nothing happens.
I dont know what the problem is... maybe i need to update my video driver, but i dont know how to do that either.
a few months ago i run it on mandriva and it worked just fine.
Hope someone can help me.

(yes... very sorry about my english).

---

### Post by mikewhatever on 2012-10-21
To just run Firestorm, you need to extract the downloaded archive first. You should get a folder called **Phoenix_Firestorm-Release_i686_4.2.2.29837**, so, assuming it's in the home folder:
```
cd Phoenix_Firestorm-Release_i686_4.2.2.29837

./firestorm
```

Creating a launcher would be a good idea as well.

---

### Post by hernan989 on 2012-10-21
i did that. I downloaded the file Phoenix_Firestorm-Release_i686_4.2.2.29837.tar.bz2 . I extracted it and i got the folder. In that folder i run the filestorm file, but nothing happens. there's some kind of error but i get no message, so i dont know. 

Now i see a black window open when i run it but immediately closes it, and i get the message saying if i wanna send a crash report. That's why i think maybe its my video drivers.

---

### Post by hernan989 on 2012-10-21
i don't know if it helps, but i run it in a terminal and it says: unable to create window, be sure screen is set at 32 bit color and your graphic driver is configured correctly.

when i go to system settings -> system -> details -> graphics. It says:
Driver: Unknow
Experience: Standard

---

### Post by hernan989 on 2012-10-21
ok.. once again, i'm don't know what to do... but i search on internet and i found this:

[B][COLOR=#073763]sudo apt-add-repository ppa:ubuntu-x-swat/x-updates 
sudo apt-get update 
sudo apt-get install nvidia-current[/COLOR][/B]

i did it and now on graphics settings it says:
Driver: GeForce 9600 GT/PCIe/SSE2
Experience: Standard
what i think it's good... but i still get the same problem and the same message on terminal (unable to create window).

I need some help.

---

### Post by mikewhatever on 2012-10-22
I am not entirely sure why you've decided to update the graphics driver. It didn't look like there were graphical errors, did it?
Anyway, here is something interesting from the [Firestorm Wiki]("http://wiki.phoenixviewer.com/fs_install_crash"):
> linux-specific

If you have just installed Firestorm on a linux system and it will not start, it is highly likely that you are missing some required libraries. You need to verify if this is the case.

You need to open Terminal and cd to the Firestorm install directory. If you are unsure how to locate it, use your linux file manager to find it first; it will help you locate the install directory. Useful shorcuts:

    ~/ - is your home directory
    ~/Desktop - is your desktop directory

so for example, from terminal, you would do something like this:

cd ~/Firestorm

Assuming that Firestorm is installed in the directory called Firestorm, in your home.

Once there, copy the following into Terminal:

LD_LIBRARY_PATH="./lib:${LD_LIBRARY_PATH}" ldd bin/do-not-directly-run-firestorm-bin 

This will spit out a long list of libraries. Check to see if any are marked as &#8220;not found&#8221;. If so, you will need to install these with your package manager.


---

### Post by Arkem5 on 2012-11-02
Are you using a 32 or 64 bits system? 32 bits secondlife viewers don't work anymore on Ubuntu 12.10 64 bits, even when you install the 32 bits compatibility packages. It has never fully worked anyway, since SL medias could play only with a 32 bits system with older Ubuntus...

Secondlife don't work anymore with opensource GFX drivers on 12.10 too, but it doesn't seem to be your case since you are using the proprietary nvidia one

Try to start the program from a terminal as explained above and copy paste the last lines when the program abort. There may be clues there to help you getting rid of the issue

---

### Post by nassah on 2013-04-07
Why graphics drivers are important? Second Life has quite a high graphics requirement to run, so checking the driver is in order is a good first move.

The above method for updating my driver to a proprietary one didn't work for me (Ubuntu 12.10) but I was able to choose an upgrade through Synaptic Package Manager.

The way of listing the libraries really helped. They weren't available in Synaptic, but I searched the names and found workarounds.

---

### Post by merc669 on 2013-04-23
> **Arkem5 said:**
> Are you using a 32 or 64 bits system? 32 bits secondlife viewers don't work anymore on Ubuntu 12.10 64 bits, even when you install the 32 bits compatibility packages. It has never fully worked anyway, since SL medias could play only with a 32 bits system with older Ubuntus...

Secondlife don't work anymore with opensource GFX drivers on 12.10 too, but it doesn't seem to be your case since you are using the proprietary nvidia one

Try to start the program from a terminal as explained above and copy paste the last lines when the program abort. There may be clues there to help you getting rid of the issue
Sorry to say that Second Life using Firestorm works just fine in Ubuntu 12.10 64Bit. Only thing that does not function is the streaming of video. Audio and all other functions work normally. One other minor bug, the "Alt" for Camera View does not work properly so you need to use "Ctrl+Alt" to move the camera in and out on a subject you are looking at. I also installed the ia32libs and uncommented out the sound card line as posted in other searches. If anybody has video working that would be great to pass along.

---

