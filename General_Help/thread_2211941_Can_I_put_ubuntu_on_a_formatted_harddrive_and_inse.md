---
title: "Can I put ubuntu on a formatted harddrive and insert it into a netbook?"
date: 2014-03-18
forum: General Help
---

### Post by shane17 on 2014-03-18
Hi,

I recently bought a netbook as a project to do up.  The problem is I'm fairly certain the screen is the only issue with netbook but I'd like make sure that it definitely the screen which is busted before I buy a new one.

There's also no harddrive in the netbook but I have a formatted 40gb sata one to use with it.  Is it possible for me to place the harddrive in a extermal case, load ubuntu on it and then place the hard drive in my netbook?

I'm hoping with ubuntu on it, it will boot as normal and I'll be able to see (using an external monitor and a vga cable) weather the netbook is indeed working, screnn aside?


Sorry that was a very long winded way of explaining my problem but hopefully someone can advise if this is possible

Thanks

Shane

---

### Post by sandyd on 2014-03-18
> **shane17 said:**
> Hi,

I recently bought a netbook as a project to do up.  The problem is I'm fairly certain the screen is the only issue with netbook but I'd like make sure that it definitely the screen which is busted before I buy a new one.

There's also no harddrive in the netbook but I have a formatted 40gb sata one to use with it.  Is it possible for me to place the harddrive in a extermal case, load ubuntu on it and then place the hard drive in my netbook?

I'm hoping with ubuntu on it, it will boot as normal and I'll be able to see (using an external monitor and a vga cable) weather the netbook is indeed working, screnn aside?


Sorry that was a very long winded way of explaining my problem but hopefully someone can advise if this is possible

Thanks

Shane

Yes, you can try that as long as Ubuntu has drivers for the netbook hardware.
I would reccomend something lighter for netbooks - such as lubuntu or xubuntu

---

### Post by westie457 on 2014-03-18
shane17 welcome.

Short answer to your question is yes.

A couple of things to be aware of though.
1) At the 'How to Install' screen choose the 'Something Else' option. You will have to specify size and type and create all partitions. Sounds pretty daunting but is quite easy to do. The hard drive will probably have the designation /dev/sdc.

2) Make certain you look to the bottom if the installer window and make sure that the location to install 'Grub' to is the 'MBR' of the hard drive you are installing to. Probably /dev/sda

---

### Post by shane17 on 2014-03-18
> **sandyd said:**
> Yes, you can try that as long as Ubuntu has drivers for the netbook hardware.
I would reccomend something lighter for netbooks - such as lubuntu or xubuntu


[QUOTE=westie457][COLOR=#000000]shane17 welcome.[/COLOR]

[COLOR=#000000]Short answer to your question is yes.[/COLOR]

[COLOR=#000000]A couple of things to be aware of though.[/COLOR]
[COLOR=#000000]1) At the 'How to Install' screen choose the 'Something Else' option. You will have to specify size and type and create all partitions. Sounds pretty daunting but is quite easy to do. The hard drive will probably have the designation /dev/sdc.[/COLOR]

[COLOR=#000000]2) Make certain you look to the bottom if the installer window and make sure that the location to install 'Grub' to is the 'MBR' of the hard drive you are installing to. Probably /dev/sda[/COLOR][/QUOTE]

That's brilliant, definitely have to give it a try.  The netbook's a [COLOR=#333333][FONT=Arial]VPCW11S1E Vaio.  Do you know if there's anyway of finding out if Ubuntu drivers exist for this model.  I did a google search but could only find stander driver packs.

westie thanks for the advice when my usb male to male lead comes in the post I'll have to give it a go. [/FONT][/COLOR]

---

### Post by slooksterpsv on 2014-03-18
That computer should work well, I'd try it and if you run into any issues with networking or that, let us know and we can try to assist you from there. Most of the drivers you'll need are most likely included in the kernel (especially if you run 13.10). I'd recommend Xubuntu or Lubuntu.

And just as a side note: I've taken Linux installed on a computer, put the drive into another (Intel to AMD) and it still worked without a hitch for me.

---

### Post by shane17 on 2014-03-19
> **slooksterpsv said:**
> That computer should work well, I'd try it and if you run into any issues with networking or that, let us know and we can try to assist you from there. Most of the drivers you'll need are most likely included in the kernel (especially if you run 13.10). I'd recommend Xubuntu or Lubuntu.

And just as a side note: I've taken Linux installed on a computer, put the drive into another (Intel to AMD) and it still worked without a hitch for me.

Hi,

Having a bit of trouble with my external sata port.  If I take out the harddrive from a laptop I have working very well (using vista) and insert my formatted drive into the laptop is there any way I could boot Xubuntu from say a flash drive and install it on the formatted hard drive, then whip it out and put the original hard drive back in.

Would my computer boot vista as normal when I return the original hard drive?

---

### Post by westie457 on 2014-03-19
That will work as well. The drive with Vista on it will work as normal when it goes back in.

Refer to my earlier post advising about partitions. You will have to allow Grub to default install to the hard drive you swapped to. This will now be '/dev/sda'

---

### Post by shane17 on 2014-03-19
Thanks again, so once I've downloaded Xubuntu  I just put it onto the dvd, plug it into the laptop with the formatted drive and then the 'how to install screen should pop up and I can follow your advice?

Sorry very new to this :)

---

### Post by shane17 on 2014-03-19
Ok I've inserted the blank drive in my laptop With a usb drive I've managed to get a to the 'something else' screen.  The problem is I keep trying to get a 'No root file system defined please correct this from the partition menu.'  I've made a particion and selected /dev/sda1 not sure what I'm doing wrong

---

### Post by westie457 on 2014-03-19
At the 'Something Else' partitioning screen did you see something like the attached picture?

At this point near to the words 'Mount Point' is a blank box. Allyou need to do is put a / in the box.
Just type it in or click on the down arrow and select.

---

### Post by shane17 on 2014-03-19
Worked a treat!  Thank you very much I now have xubuntu up and running on the net book, now just have to source a cheap screen :)

---

