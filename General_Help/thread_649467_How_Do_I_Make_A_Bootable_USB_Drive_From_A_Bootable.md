---
title: "How Do I Make A Bootable USB Drive From A Bootable CD?"
date: 2007-12-24
forum: General Help
---

### Post by xluryan on 2007-12-24
I have a bootable CD and I'd like to convert it over to a bootable USB drive. How would I do that?

---

### Post by xelapond on 2007-12-25
I don't know what you mean by convert it over, but you can install linux/ubuntu on a flash drive.  Just beware that flash memory cannot withstand as many write cycles as a hard drive, so you might kill your flash drive eventually.

Try this link:
[http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar](http://www.debuntu.org/how-to-install-ubuntu-linux-on-usb-bar)'

Hope that is relevant to your situation.

---

### Post by xluryan on 2007-12-25
Kind of... but it's not ubuntu I want on my flash drive, it's the contents of the CD. Isn't there some way to just copy the cd to the flash drive and boot from the flash drive?

---

### Post by xelapond on 2007-12-28
It really depends on what it is your are trying ot boot.  Is it a custom CD you made? Do you have to copy the contents of the CD?

---

### Post by bodhi.zazen on 2007-12-28
It is hard to give specific advice without additional information.

See if this site helps : [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

---

### Post by motoperpetuo on 2008-03-23
i'd like to know how to make my flashdrive bootable so that i can put an MS-DOS image on it and run the BIOS upgrade (which is a DOS/Windows executable) for my new computer. My machine is a Dell Inspiron 530 preinstalled with Ubuntu, which, you would think, would work well with Linux. But oh, does it have problems, and I'm hoping to resolve them by updating the BIOS,which, again, can only be done from DOS or Windows. Thanks, Dell. Thanks a whole lot.

---

### Post by knutschr on 2008-03-23
> **motoperpetuo said:**
> i'd like to know how to make my flashdrive bootable so that i can put an MS-DOS image on it and run the BIOS upgrade (which is a DOS/Windows executable) for my new computer. My machine is a Dell Inspiron 530 preinstalled with Ubuntu, which, you would think, would work well with Linux. But oh, does it have problems, and I'm hoping to resolve them by updating the BIOS,which, again, can only be done from DOS or Windows. Thanks, Dell. Thanks a whole lot.

?? A new machine not working?
How can that be?
What is wrong?
Why can't you just ask for another machine (of the same kind) that works?

---

### Post by motoperpetuo on 2008-03-23
> **knutschr said:**
> ?? A new machine not working?
How can that be?
What is wrong?
Why can't you just ask for another machine (of the same kind) that works?

i'm guessing that it's a flaw that's common to all of the newer machines of this model. if they could test a machine for me and confirm that it works, i would gladly accept it as a replacement. btw, i figured out how to make a bootable USB flashdrive that boots into DOS. here are the instructions, in case they help anyone out:


1)Download and install the HP Drive Key Boot Utility from [http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=MTX-UNITY-I23839&jumpid=reg_R1002_USEN](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?lang=en&cc=us&swItem=MTX-UNITY-I23839&jumpid=reg_R1002_USEN)

2)Download a MS-DOS image file (.img extension) from [http://www.allbootdisks.com/download/dos.html](http://www.allbootdisks.com/download/dos.html)). I used the DOS 6.0 image, but I suppose any of them would work.

3)Insert your USB key and run the above HP Drive Key Boot Utility (from Windows, of course).

4)Choose the drive letter for your USB key and click Next.

5)Keep the default “Create New or Replace Existing Configuration” option and click Next.

6)Choose the Floppy Disk option and click Next.

7)Browse to the DOS image you downloaded and click Next.

If everything went well, you'll have your bootable DOS USB flash key now.

you need a windows computer to do this. you can use the same utility to make a bootable flashdrive that doesn't act like a floppy disk.

unfortunately for me, although i am now able to run the BIOS update that supposedly works this way, it errors out with a cryptic "Error! udosexe = -5". back to the drawing board. i may try the same thing with a windows 98 boot disk image and see if i have better luck. needless to say, Dell is not my favorite company in the world right about now.

---

### Post by JacekZ on 2008-04-16
motoperpetuo,
You might be interested that I get the same error on a 530n, but in this case I'm not using a memory stick, but the method suggested here:

[http://www.felix-schwarz.name/Flashing_a_Dell_Bios_with_Linux_%28en%29]("http://www.felix-schwarz.name/Flashing_a_Dell_Bios_with_Linux_%28en%29")
[http://linux.dell.com/projects.shtml#biosdisk]("http://linux.dell.com/projects.shtml#biosdisk")

..albeit I'm doing this with Fedora 8.  I'd read about memory sticks and it seemed too difficult for me, this seemed easier.  Anyway it leads me to conclude that if you are having trouble with a dos based approach, and I'm having trouble with a linux based approach (which I think uses a dos image), then I need to go back to Dell on this?  It can't possibly be right that one should install XP or such like.

Jacek

---

### Post by Entity` on 2008-04-23
Since this is relevant, I shall state my question here.  How do I cause a USB drive to ACT as a CD-RW/DVD-RW drive.  Im tired of spending money on CD-Rs and CD-RWs, so I figured, why not use my usb drive as a cd.  Its been done before, and its more reliable, there's much less risk of damaging data this way.  I also believe that was the original question of the thread if I read right.  Quote me if im wrong.

---

### Post by dcstar on 2008-04-25
> **Entity` said:**
> Since this is relevant, I shall state my question here.  How do I cause a USB drive to ACT as a CD-RW/DVD-RW drive.  Im tired of spending money on CD-Rs and CD-RWs, so I figured, why not use my usb drive as a cd.  Its been done before, and its more reliable, there's much less risk of damaging data this way.  I also believe that was the original question of the thread if I read right.  Quote me if im wrong.

You plug in your USB drive and write to it as you would with any filesystem.

And the original question is about **Bootable **drives, for a bootable version of the Ubuntu CD/DVD you would do this:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by MentalNotes on 2008-04-26
Dell offers packages to update your BIOS from Ubuntu. See this post on the Direct2Dell blog here: [http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx]("http://direct2dell.com/one2one/archive/2007/12/05/37446.aspx"). I do have to say though, I have never used it.

If you want to go down the DOS route I don't think DOS has USB support so you might want to look at FreeDOS. I haven't tried booting it from USB.

---

