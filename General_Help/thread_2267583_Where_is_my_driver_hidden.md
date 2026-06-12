---
title: "Where is my driver hidden"
date: 2015-03-02
forum: General Help
---

### Post by Nina_W on 2015-03-02
I'm running Ubuntu off a memory stick and needed to download a Broadcom driver for my wifi. But I have to tell it to find the driver every time I boot up. I imagine this is because the driver has gone somewhere on my hard driver rather than the memory stick.

So, how do I find where it has put itself and how do I fix it so it automatically sees it rather than me having to tell it to go and find it?

---

### Post by kc1di on 2015-03-02
Hello Nina_W and welcome to Ubuntu,

I'm not sure I'm reading you correctly so let me clarify what your saying.  Do you have ubuntu installed to a usb stick or have you just burn a live session on the stick.
if it a  live session then any changes you make will not be saved on reboot.  if this is a persistent full install then any drivers would have been installed on the Ubuntu partition not the hard drive.  

There is a way to make a live usb with persistence -- you can find out how in [this wiki ]("https://wiki.ubuntu.com/LiveUsbPendrivePersistent")

Let me know how you install Ubuntu to the usb and I'll try to sort out how to make the driver work for you.

---

### Post by steeldriver on 2015-03-02
Hello and welcome to the forums

Can you explain a little more what you mean by "tell it to go and find it"? is this a command you're entering? if so what is it please

Also, did you enable persistence on the USB when you created it?

---

### Post by Nina_W on 2015-03-02
I put ubuntu on my memory stick with instructions from here  [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)
I'm not sure what you mean by live session. I run it from the memory stick, ie. on boot up I tell the PC to boot from USB. I then save all my files on the memory stick so that I can take "my computer" with me on a memory stick. (At least that was the idea!)

Once running ubuntu I have to Select "System Settings" then "Software and Updates" then "Additional Drivers"
It then says "Searching for drivers" then it shows the Broadcom Corporation thing and says its not working and gives me an option of using the Broadcom driver it has found.
I tried to paste the screen shot in here but there doesn't seem to be an option.

---

### Post by kc1di on 2015-03-02
Ok according to that page -- you were asked to set a persistence space.  Did you do that?  

If so how big is your usb drive , the instructions say 2 GB but that is way to small for a full install of ubuntu. 

Most people burn the .iso image to a DVD or USB stick using a DVD Burning tool or a usb burning tool such as unetbootin. with burn a live /demonstration copy of ubuntu.
it can be run live without actually installing the system on your machine.  but if you did it that way , changes and files created are all lost when you reboot the system. 

If you in fact install your copy in persistence mode - and can save files to the usb stick then the Driver should be installed. and should not have to re-install every boot. 

but again 2GB USB is not big enough to hold a full install of ubuntu. 
I suspect you did not set the persistence mode size or your USB is not large enough to accommodate adding any packages.

---

### Post by Nina_W on 2015-03-03
Its a while back since I did it. I can't remember if I set a persistence space or not. I remember having some difficulties following some bits because I went to the wrong page first, where the search engine directed me. I thought I was starting at the beginning when I was actually starting part way through!

So, I'll try again from scratch. The USB is 4Gb so should be enough.

Thanks for the help.

---

### Post by kurt18947 on 2015-03-03
The reason a small flash drive works for a live USB is that the files are in a compressed format. For what you want to do, a 'real' install might be a better idea.  I try to use a flash drive with a flashing LED, that way you know it hasn't stalled during the install process because a screen may not change for several minutes. I just did a Mint 17.1 install and used a 16 GB. flash drive. The O.S. took 6 GB+ leaving a bit less than 10 GB for additional drivers, updates, data etc. I've never had any success updating a live USB, it would become corrupt rather quickly. I've never tried to install additional drivers on a live USB so have no idea how that'd work.

It is of course possible to install a 'real' install on a flash drive without messing with any hardware. Someone who is inexperienced with partitions though can easily overwrite their existing O.S. and data with a wrong click. The safest way IMO to create a 'real' install on a flash drive is to first create live media, either DVD or USB drive. Then shut down the PC and unplug (desktop) or remove (laptop) the hard drive(s). Desktops are typically easier, just remove the cover and unplug. Removing the hard drive from a portable may be as simple as removing a couple screws and a cover or door or it may involve significant disassembly depending on the machine. Load both the live media and a large enough flash drive. You may have to tell your machine to boot off the live device or it might do so by itself. After the live session has loaded, there should be a desktop icon to install the O.S. Click that and it should find the blank USB drive as a install destination.

I partition manually though that's a personal choice. My machines have 2 GB+ RAM so I don't create a swap partition though I guess you could. Flash drives typically come formatted FAT32, I typically chose ext4. If you don't create a swap partition, you'll get a screen asking if you want one. I usually decline though it'd be wise to create swap if you're using the device on low RAM machines. Once partitioning is complete it's not much different than installing Windows. 

It will take quite a long time because writing to the flash drives found in most retail stores is pretty slow, much slower than reading from them. Once written shut down the live session, remove the live DVD/USB and reboot. You should have a fully functional though somewhat slow *buntu install. If I can use a wired network connection I do so. I find wired network connections faster and more reliable than wireless and there are seldom connection issues. Run the software updater which again may take some time, install 3rd party drivers if required, reboot and you should have a fully functional though slower than a hard drive install. If you're moving this device between machines, I would not install any 3rd party video drivers. Booting a flash install with Nvidia video drivers installed may fail if booted on a machine with AMD video for example. There should be no problem with the default video driver selected. This is a bit lengthy but hopefully will be of some use.

---

