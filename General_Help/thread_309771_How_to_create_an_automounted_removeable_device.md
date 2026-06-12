---
title: "How to create an automounted removeable device?"
date: 2006-11-30
forum: General Help
---

### Post by johnpipe on 2006-11-30
I have the same problem with Edgy as I had with my KNOPPIX 3.7 traditional Debian-style install, namely the digital camera did not automount when connected.  In Knoppix debian I found the program "automount" in use, so was able to find the right documentation and get automounting of the camera working.

In Edgy, however, 

```
johnpipe@linus:~$ apropos automount
automount: nothing appropriate.

```

So, how does one set up a removeable mass-storage device to automount in Edgy? What options are needed in /etc/fstab? I can manually mount with

```
sudo mount /dev/sda1 /media/usb
```

so I verify that works; however, it does not then have auto unmount, either, which is really inconvenient with a battery-powered camera.

Another related thing, I wasn't previously aware of dynamic device creation; I notice that /dev/sda(*n*) only exists when such a device is actively connected. Where can I read-up on this system feature?

Thank you, Johnpipe

---

### Post by cronholio on 2006-11-30
Ubuntu does auto-mount removable mass storage devices since Hoary or probably even before. I know this doesn't solve your problem, I just wanted to let you know that it's not a feature you have to setup.

What happens if you plug in a USB stick or external HDD? If it auto-mounts, it has something to do with your camera and I would suggest a Google search on the Camera name plus "Ubuntu".

---

### Post by reclusivemonkey on 2006-11-30
Try looking in the "Default Applications" on your Preferences Menu. There should be an entry for Cameras. When I plug my digital camera in, it asks if I want to import photos, but it doesn't show an icon on the dekstop.

---

### Post by johnpipe on 2006-12-02
There is no "Default Applications" in  Edgy preferences.  The tab for  cameras is under "Removeable Drives and Media"; my Fuji camera is exactly the same thing as a USB stick, they are both seen as hard drives by the system, so the pertinent tab is "storage", and everything pertinent is checked:

Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted

 The camera tab there has only a checkbox for "Import digital photographs when connected", and the browse button asks you to "select program to import photos"; unfortunately, it drops the user into his own home directory, which is useless in terms of non computer-tech people (I'm not one of those, I've installed several linux versions as well as FreeBSD, compiled my own kernels, etc.) such as the ordinary user toward whom Ubuntu is professed to be aimed. The camera tab therefore has nothing directly to do with mounting the camera.

But, it is not working here.  There is nothing wrong with the camera, it automounts no problem on Knoppix live, automounts on my knoppix-debian HD install since setting up the scripts, mounts with no problem on the CL in Edgy (and, automatically puts the icon on the desktop even when hand-mounted!).  If the camera doesn't automount, a USB stick won't either.

There are many things not working smoothly in Edgy, this is one of them, and that's why it's called "Edgy"! :rolleyes:

Regards, Johnpipe

---

