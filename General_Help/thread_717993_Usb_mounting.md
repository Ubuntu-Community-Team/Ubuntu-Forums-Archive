---
title: "Usb mounting"
date: 2008-03-07
forum: General Help
---

### Post by jnzooger on 2008-03-07
Ok, bear with me, this might be confusing.

There is a tool for that other OS that shall not be named that will mount anything in a particular physical port to the drive letter you specify. (ex: Port 1 is always X:, Port 2 is always Y:) This is what I need to do in Linux.

I have two usb ports and two pre-made mount-points (/mnt/USB1 and /mnt/USB2). I need to make it so that no matter what or when a usb mass storage device is pluged into usb1, it mounts to /mnt/USB1 and same for usb2 with /mnt/USB2. 

For example, say I have one thumb drive. If I plug it into usb2, it mounts to /mnt/USB2, but if I imediately remove it and plug it into usb1, it needs to mount to /mnt/USB1 without any config changes.

----------------------------------

Edit: The program refrenced above is called USBDLM. It uses an ini file with: > [DriveLetters50]
PortName=3-1-1
Letter1=X to setup usb port 3-1-1 as drive X: no matter what is pluged in, unless the particular device is defined in the ini to mount elsewhere.

---

### Post by fragos on 2008-03-07
You want a consistent mount point for each USB storage device.  The solution is to place a disk label on the storage device.  It will always be monted as /media/{label} regardless of the physical port.  You can futher control the mount points by writing UDEV scripts.

---

### Post by jnzooger on 2008-03-07
> **fragos said:**
> You want a consistent mount point for each USB storage device.  The solution is to place a disk label on the storage device.  It will always be monted as /media/{label} regardless of the physical port.  You can futher control the mount points by writing UDEV scripts.

That would be easy, but it is not what I need.

I need a consistent mount point for each usb *port*. This way, if a device is pluged into usb1, it mounts to usb1, and if same device is pluged into usb2, it mounts to usb2.

This is for an arcade cabinet where one port is player 1 and the other is player 2. I have to have it be possible for someone to play on player 2 without a player 1 and have it possible for player 1 to plug in his/her memory card after player 2. Also, it needs to be possible for the person who played as player 1 yesterday to play as player 2 today with the same memory card.

I would hate to have to go to the micro-side for this cabinet. [-(
------------
Off topic: How's Fresno these days? I'm up in Merced. :-)

---

### Post by dcstar on 2008-03-08
> **jnzooger said:**
> That would be easy, but it is not what I need.
........

You were advised to look at the UDEV scripts, that is the only place you may find the answer. I doubt anyone else is going to to this sort of complicated work for you.

---

### Post by jnzooger on 2008-03-08
I was advised under incorrect asumptions about what I need. I looked at some sample UDEV scripts and couldn't find anything like what I'm looking for. If I knew how to write the script, I wouldn't be asking for help, and likely I would post the script for others to use. 

I know it is posible and has been done in Linux. However, the person who I know made it work is being elitest and refuses to help. 

I'm not sure why this should be complicated. There are already ways to show what port the device is pluged into.

---

### Post by fragos on 2008-03-08
If what you need isn't available for free you can purchase the help from an expert.  Your requirements are after all for what appears to be a commercial application.  Might I suggest you contact [http://www.ubuntu.com/support](http://www.ubuntu.com/support).  They list many sources of support including paid.

---

### Post by jnzooger on 2008-03-08
Thanks, I'll look into that. 

This isn't a commercial application though. I'm just making this cabinet for a friend who wants it as accurate as possible. 

The main reasons for using linux come down to instant loading of the program without a shell, and mounting special folders other than default locations. I'm also looking at coreboot to make the computer boot in under 10 seconds. 

With win2k, I'd have to load explorer at least, all folders mount at a predictible spot (I can't change them), and coreboot can't speed up the nearly minute long boot. However, USBDLM would mount flash-drives correctly.

---

