---
title: "[SOLVED] Suspend &amp;amp; hibernate laptop mode"
date: 2007-10-01
forum: General Help
---

### Post by juantastico on 2007-10-01
Hello,
when ever i click on suspend my laptop (Acer 5610z) it will shutdown, but then when i click the keybord it will start again but the only thing i can se is the mouse pointer on a black screen.

Do you have any sugeestions? on how to solve this issue


MANY THANKS !

---

### Post by ramjet_1953 on 2007-10-01
How much memory do you have?

How big is your swapfile?

Regards,
Roger 8)

---

### Post by juantastico on 2007-10-01
I have 2 gig ram and swap file 512 i have ubuntut 7.04 and and a nvida 128meg go 7300 video card

---

### Post by ramjet_1953 on 2007-10-01
You may need to increase your swapfile size, as an image of your current working environment is stored there when you suspend / hibernate.

As a general rule around 1 Gig max is enough, but if you leave memory intensive applications open, or have several open, you may need more. 

Hopefully this will help, but Suspend / Hibernate can be a problem with some laptops.

Regards,
Roger :cool:

---

### Post by juantastico on 2007-10-01
Hi roger,
How do i increase the swap file is there an easy way, since a am a noob when it comes to this this things.

thanks

regards

---

### Post by ramjet_1953 on 2007-10-01
OK, this may be a bit scary, but you need to change the swapfile size by using parted.

Many newcomers make the mistake of trying to change partition sizes while running Linux. You can't do it that way, as the drive is mounted and cannot be altered.

By far the easiest way to fiddle with partition sizes is to download the GPartEd LiveCD.

It is an iso that you burn to a CD SLOWLY (no faster than 4 X) and then boot from the CD.

It is a graphical interface and is easy to use.

You will need to take a little space from an existing partition that has plenty of room and transfer it to your swapfile partition.

Here is the link for the GParted LiveCD download.

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

I also suggest that you have a good read of the documentation first.

If you still feel uncomfortable, come back to this forum and we'll walk you through it.

Please understand that this may not fix your problem, but even if it doesn't, you will have learnt a lot about how to partition a hard drive.

Regards,
Roger :cool:

---

### Post by juantastico on 2007-10-01
Thank you Roger i will try your recomendatios after my course :) 
Many thnaks for your help

I will post my results no later than tonight 


:guitar:

---

### Post by juantastico on 2007-10-01
Hi Again Roger,

I did what you told me i transfer the amount needs so the swap has 1 gig (It took only 4 hours lol). But unfurtanabetly i still experience the same effects in the suspend mode.

Do you have any other suggestions like changing my video driver or something else?

cheers:)

---

### Post by juantastico on 2007-10-01
Some please:popcorn:

---

### Post by CalvinK on 2007-10-02
> **juantastico said:**
> Hello,
when ever i click on suspend my laptop (Acer 5610z) it will shutdown, but then when i click the keybord it will start again but the only thing i can se is the mouse pointer on a black screen.

Do you have any sugeestions? on how to solve this issue


MANY THANKS !

You can test the uswsusp software (you can download it by Synaptic) which is used by Ubuntu. Then test s2ram -force in a console then s2disk or s2both. If s2ram -f works, then you can go into 
sudo gedit /usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
and in lines that say:
elif [ -x "/sbin/s2ram" ] ; then
/sbin/s2ram 
add -f to force suspend after s2ram. 

If s2disk works, goto
 /usr/lib/hal/scripts/linux/hal-system-power-hibernate-linux  and check for s2disk. (Unfortunately, it doesn't work on my Toshiba A200 laptop).

:lolflag:

---

### Post by juantastico on 2007-10-02
Hi Calvink,
I tried installing the software you recomend but i get this message

Currently userspace software suspend can write only to a swap partition. Your system doesn't seem to have such a partition. Please make one, preferably with twice the size of your physical ram. Then run dpkg-reconfigure or setup the configuration file yourself.

This is weird since i have a 1 gig swap file. Also after installing the program i do not where to acces it. Any suggestions?

I really appreciate your help and sorry for my noobenes i am tring to get things straight

cheers

---

### Post by CalvinK on 2007-10-03
> **juantastico said:**
> Hi Calvink,
I tried installing the software you recomend but i get this message

Currently userspace software suspend can write only to a swap partition. Your system doesn't seem to have such a partition. Please make one, preferably with twice the size of your physical ram. Then run dpkg-reconfigure or setup the configuration file yourself.

This is weird since i have a 1 gig swap file. Also after installing the program i do not where to acces it. Any suggestions?

I really appreciate your help and sorry for my noobenes i am tring to get things straight

cheers
I've not had this problem but, in your case, I would check my fstab file for my swap partition. Is it recognized by gparted or fdisk -l ? If yes I would check the following conf file.

/etc/uswsusp.conf. You may find something like this :

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda4   <---*** verify that this corresponds to your swap partition***
compress = y
early writeout = y
image size = 2025000000  <---* here my modification with the size of my swap partition*
RSA key file = /etc/uswsusp.key
shutdown method = platform

For the size of the swap partition I think that 1.5 x size of your ram is good enough but my swap only has 1.0 x ram. You can resize it with gparted (on a CD-rom only with your HD unmounted).

I hope it works for you. You can access the program in a console by typing s2ram or s2disk:)

---

### Post by juantastico on 2007-10-04
Hello again, 
I have good news, i decided to try the Gusty beta version 7.10 and now both the suspend and hibernate modes work perfect.

Thanks for your help

---

