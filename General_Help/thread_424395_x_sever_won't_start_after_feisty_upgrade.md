---
title: "x sever won't start after feisty upgrade"
date: 2007-04-26
forum: General Help
---

### Post by tyler_roach on 2007-04-26
I'm having terrible trouble after upgrading to Feisty from Edgy -- my xserver won't start no matter what I do. (a splash screen will appear and then I get a text login) I am using an ATI Radeon 9250 card, and have reconfigured the xorg.conf file numerous times - manually and with dpkg-reconfigure, choosing ati, fglrx, and vesa drivers, all to no avail. What's more, when I remove my ati card and try to use the embedded via one, it won't start either, no matter how many times I reconfigure xorg.conf. The only thing that works (this is what I'm doing now) is *deleting*  the xorg.conf file and going without, using the embedded card. This works, but not optimally.

The error that repetitively appears in my xorg.0.log file is 'no screen found,' which is baffling, since I have done lspci and manually made sure everything is properly set up.

Can anyone help me? Thanks in advance.

---

### Post by sevencapitalsins on 2007-04-26
I used to have an ati radeon 9250 but gave up trying to set 3D up after a week of massive fighting (now I'm an nVidia user)

First of all, there is a way to use your pc and making changes to the configuration without being "shut off": you can use a liveCD, mount your hard disk on, let's say, /mnt/sda and then chroot into it.

```

sudo mkdir /mnt/sda
sudo mount -t ext3 /dev/YOURHDD /mnt/sda
sudo chroot /mnt/sda

```

About your problem: I suggest to take a brand new xorg.conf with vesa drivers. Try then ATI drivers. But as far as i know your card is NOT supported. (that was why i bought an nVidia)

Can you post your xorg.conf if it is still not working?

Also, you may want to see that your sources.list doesn't contain non-Ubuntu repositories: try commenting out the non-standard ones, then do apt-get update, apt-get upgrade, apt-get dist-upgrade, apt-get -f install. If  during this you see that some X files are rewritten, well maybe you've solved the problem.

Bye,
Luca

---

### Post by phidia on 2007-04-26
Can you disable the onboard video in your bios? If you can then do that and re-install the agp card and try again.

---

### Post by tyler_roach on 2007-04-26
> **phidia said:**
> Can you disable the onboard video in your bios? If you can then do that and re-install the agp card and try again.

I don't think I can disable the onboard video, but it seems to get disabled automatically when I put the agp in. But regardless, x won't even start normally with the onboard chip, as I said. The only way it will start is by *TOTALLY REMOVING THE XORG.CONF FILE*, and booting with the onboard chip. (X will also start with the ati card once I *TOTALLY REMOVE XORG.CONF*, but although I can hear the Gnome drumbeat, my monitor says "input not supported" and I can't see anything.)

What I would like is to have a working xorg.conf, like everyone else.

And afaik, my card is supported,  -- it worked marvelously with edgy.

Thanks.

---

### Post by phidia on 2007-04-26
It looks like ati has a driver for your card [http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html](http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html)

---

