---
title: "Help No music on iPod touch"
date: 2008-01-02
forum: General Help
---

### Post by omega101 on 2008-01-02
I followed the wiki page to mount the iPod on ubuntu 7.10.   Now gtkpod and amarok see the iPod and  it can send files , but now the iPod can't see any music. I'm having a really hard time configuring the iPod to work on Linux and sometimes the iPod won't even mount.  I'm new to Linux so go easy on me when trying to explain stuff becuase the terminal is becoming an fruastrating tool to use.


thanks

---

### Post by omega101 on 2008-01-03
can anyone help me please

---

### Post by itsJim on 2008-01-04
I'm having the same problem. I have uploaded songs on to my ipod touch using gtkpod but my ipod doesn't see them.

---

### Post by mwacky on 2008-01-04
Have you guys considered looking at the setup for the IPhone, the Touch is very similar to the Iphone, so perhaps this will help:

[https://help.ubuntu.com/community/Po...Devices/iPhone]("https://help.ubuntu.com/community/Po...Devices/iPhone")

Also look at this thread for more info:

[http://ubuntuforums.org/showthread.php?t=588246&highlight=Ipod]("http://ubuntuforums.org/showthread.php?t=588246&highlight=Ipod")

My touch hasn't arrived yet, so I haven't tried myself, but the Community Docs are very reliable and the thread offers many link to investigate.

---

### Post by itsJim on 2008-01-06
Using Amarok from the sources in the wiki seems to be working for me

---

### Post by radbadhappy on 2008-01-07
I had the same problem until I discovered that I had accidentally left of the *0x* from the front of the 16 digit hexadecimal GUID when I put it into the **SysInfo** file.

I fixed it from my desktop in the following way:

mount the ipod:
[FONT="Courier New"]ipod-touch-mount[/FONT]

open the file for verifying that the GUID matches:
[FONT="Courier New"]gedit /media/ipod/iPod_Control/Device/SysInfo[/FONT]

get the GUID again as described in the ipod wiki ( [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) ):
[FONT="Courier New"]sudo lsusb -v | grep -i Serial[/FONT]

and unmount the ipod:
 once the SysInfo file is correct, disconnect the ipod from amarok or gtkpod, and unmount the ipod, then remount it.

I hope this helps!

---

### Post by FRuMMaGe on 2008-02-01
> **radbadhappy said:**
> I had the same problem until I discovered that I had accidentally left of the *0x* from the front of the 16 digit hexadecimal GUID when I put it into the **SysInfo** file.

I fixed it from my desktop in the following way:

mount the ipod:
[FONT="Courier New"]ipod-touch-mount[/FONT]

open the file for verifying that the GUID matches:
[FONT="Courier New"]gedit /media/ipod/iPod_Control/Device/SysInfo[/FONT]

get the GUID again as described in the ipod wiki ( [https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone) ):
[FONT="Courier New"]sudo lsusb -v | grep -i Serial[/FONT]

and unmount the ipod:
 once the SysInfo file is correct, disconnect the ipod from amarok or gtkpod, and unmount the ipod, then remount it.

I hope this helps!
Thank you so much!

---

### Post by pythonusr on 2008-03-16
Alright, I can't even issue "sudo lsusb -v | grep -i Serial", because my iPod isn't recognized by lsusb.

What's wrong here?

---

### Post by FRuMMaGe on 2008-03-16
> **pythonusr said:**
> Alright, I can't even issue "sudo lsusb -v | grep -i Serial", because my iPod isn't recognized by lsusb.

What's wrong here?

This may sound stupid, but is it actually plugged into the usb port?

---

### Post by pythonusr on 2008-03-16
Yeah, and it's seen by dmesg.

```
> [10277.488656] usb 5-3: new high speed USB device using ehci_hcd and address 6
> [10277.623742] usb 5-3: configuration #1 chosen from 3 choices
```

---

### Post by pythonusr on 2008-03-17
> **pythonusr said:**
> Yeah, and it's seen by dmesg.

```
> [10277.488656] usb 5-3: new high speed USB device using ehci_hcd and address 6
> [10277.623742] usb 5-3: configuration #1 chosen from 3 choices
```

This might actually be because I'm not using ipod-convenience, so it hasn't set the FirewireGUID. But since I can't see it by USB, I can't set it.

Maybe if I connect it to iTunes and sync once on my Windows machine, it'll fix it. Worth a shot.

---

### Post by Gundamironfist on 2008-03-17
Ok, so I'm having the same troubles only gtkpod and rythmbox can read the files from my iPod, and I can even write files using either program, but when I eject my iPod All of my files are gone, even the files I had before I hooked it into the system. When I reconnect back to my system (after restarting the system) my files can be read by both programs, but whenever I disconnect my iPod all of my music files disappear. I have always disconnected my iPod correctly, and I am trying to learn Ubuntu and what it can do for me, but when this happened I became kinda angry with Apple for not making an iTunes for Linux... What should I do?:(

---

### Post by pythonusr on 2008-03-17
Alright, I restored the iPod, and it still can't be seen by "lsusb". It's pissing me off, a lot. I'll try syncing once with my Windows computer.

---

### Post by Sudo Sumo on 2008-03-25
I had a similar problem with my nano video 8 gig; i transferred music, but my iPod said there wasn't any (although I could play it docked).

Apparently, the default music player for ubuntu which launches when you connect an iPod doesn't write to the iPod's local db very well, causing it to read nothing.

This software helped me out:

[http://www.redchairsoftware.com/anapod/support/regassist.php?c=0401](http://www.redchairsoftware.com/anapod/support/regassist.php?c=0401)

Look for the bit about rebuilding the db.

Unfortunately, it seems only to run on windows, but I was able to use a virtual instance of Win2K to download the trial and rebuild my iPod's db.

Lesson?  Don't use the default player to transfer music!

---

### Post by aaraguz on 2008-03-28
Hi everyone,

I bought an iTouch 8 Gb last week. I only use Ubuntu at home, so I went through all the process: jailbreaking, login via ssh passwordless, mounting it with Amarok...Up to here everything fine, but, like many other people I can't see the transferred songs in the iPod.

I followed the methods explained, retrieving the firewire with 
"/usr/sbin/ioreg  -n IOIpodUSBDevice  -w 0 | grep DeviceConfiguration | cut -d '"' -f 44 | cut -c 1-16 "
and then i pasted it into the "/media/ipod/iPod_Control/Device/Sysinfo" file which now looks like
"FirewireGuid: 0x48b3b077496173f3". Nothing else written on it. I think first time i edited the file, there was another line...

Anyone can tell me how the Sysinfo should look like?

Anyone knows other possible fix to the froblem in case the Sysinfo is correct?

I read somewhere that i should uninstall libpodgtk and amarok, and buiding them back again in my PC. Thas it make any sense? how do you do that? I never compiled a source before.

Pleasssssssssssssssssse help!!!

---

