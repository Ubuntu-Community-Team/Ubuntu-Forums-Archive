---
title: "Backing up Virtualbox installs?"
date: 2012-11-05
forum: General Help
---

### Post by sr_guy on 2012-11-05
System info:

AMD Dual Core CPU
4GB RAM
120GB HDD
Ubuntu 12.04 X64

I've been using Ubuntu for years now. Windows doesn't exist on my machines. :) Anyway, I wan to experiment with other Linux distros, and if possible install all wanted software, configure system, and setup a Media system with other distros. However, I do not want to have to wipe everything, and use multiple partitions for installs, it's too much of a hassle if I want to beta test. I normally use Clonezilla to image and backup locally or over my network, but even doing that is a bit of a hassle just for testing distros.

So I was wondering if there was a way after installing and setting up an OS in virtualbox if there was a way to image the virtualbox install?

---

### Post by bob-linux-user on 2012-11-05
You can "export an appliance" and then re-import it later.

---

### Post by gerowen on 2012-11-05
> **bob-linux-user said:**
> You can "export an appliance" and then re-import it later.

I was just about to say that.  You can export them to a file, stick the file on an external if you're worried about space, then remove them from your Virtualbox setup, and import those appliance files on any machine running VirtualBox.

---

### Post by sr_guy on 2012-11-05
There is no way to image the virtualbox setup to install and run on a live system?

---

### Post by gerowen on 2012-11-05
> **sr_guy said:**
> There is no way to image the virtualbox setup to install and run on a live system?

You could set up a virtual machine, then boot that machine from a Clonezilla ISO and attach an external hard drive to store the image on, then forward the USB connected external drive to the running virtual machine, and it should allow you to make a Clonezilla image.  If it's a Linux OS you should have no issues restoring an image made this way to a machine as long as the processor architecture is the same (x86, x86_64, ppc, etc.) and you don't go installing too many proprietary drivers that may conflict with different hardware configurations.  For example if you install the proprietary ATI drivers and Xorg gets configured to use it, and then you restore that image to a machine with an NVidia card, you may find yourself with no video until you reconfigure Xorg manually from the terminal.  For Windows virtuals though, they get really picky about hardware changes, and you probably won't have much, if any luck restoring a Windows OS created this way to an actual computer.  Even if they do boot, they'll probably ask you to re-register them as "Genuine".  Linux OSs, in my experience, are very forgiving in situations like this and will often re-configure themselves on the fly when they start up if they detect new hardware.

---

### Post by sr_guy on 2012-11-05
It won't be Windows. It'll be distros like Arch Linux. Stuff like that.

---

