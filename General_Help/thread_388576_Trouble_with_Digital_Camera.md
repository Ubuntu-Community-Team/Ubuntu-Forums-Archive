---
title: "Trouble with Digital Camera"
date: 2007-03-19
forum: General Help
---

### Post by geovino on 2007-03-19
I have a Canon powershot A530. When I plug it in to the usb cord to download to my hdd I get this error message:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Do I have to mount this device ahead of time?

---

### Post by teddmeister2 on 2007-03-19
hi.

---

### Post by fragos on 2007-03-19
By default, Ubuntu will recognize the camera and popup a prompt to download images of Ignore.  Ignore will mount the memory card as if it were placed in a USB card reader.  System-> Preferences-> "Removable Drives and Media", including Cameras, controls what what applications if any will be involved when new meadia is inserted.  Perhaps examining it will point to a cause.

---

### Post by geovino on 2007-03-20
I went into removable media and checked off two more options, it still didn't change the error message. I can't see what else to do. I sees my camera but won't import. What does that error message mean? Is there another file that is needed?

It's works fine on my older pc with Ubuntu, but not on this newer pc!

---

### Post by fragos on 2007-03-20
The message indicates that access to your camera may be blocked because because another process already has mounted that port.  It can't be mounted again without the other process unmounting it.  It doesn't identify the other process but does give you another angle to check into.  Nemely, what other process has mounted that port?  Have you for example modified any udev rules?

---

### Post by geovino on 2007-03-20
Haven't modified any files. I'll run it again and see what the error message says this time and I'll look and see what other processes in System Monitor are running that are getting in the way.

I tried again... here's what I get:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

I doesn't give me any clues! I look in system monitor and I don't see what could be in the way!

Any clues?

---

### Post by fragos on 2007-03-20
Mount points are usually root owned and have a group permission.  Membership in the group gives the user access.  Off hand, I don't know what mount point is assigned to a camera but you would need to be group member to access the camera.  Have you tried any other USB connected storage like an SD card reader?  What USB devices do you have that are plugged in when this happens?  What applications are open?

---

### Post by Herbt on 2007-03-21
This sounds very much like this bug(s)

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532)
[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/64146)

going through the thread, I have not found the right combination to solve the problem, though some have.

There are whole threads I haven't dug into yet though, like this one 

[http://ubuntuforums.org/showthread.php?t=286730&highlight=kodak](http://ubuntuforums.org/showthread.php?t=286730&highlight=kodak)

---

### Post by llamakc on 2007-03-21
I ran into this problem also. 

Here's what worked for me (something I found off of launchpad)

I edited the /etc/udev/rules.d/45-libgphoto2.rules file, commenting out the 3rd line below, and adding in the fourth one.

```

# udev rules file for libgphoto2 devices (udev < 0.98)
#
#BUS!="usb*", GOTO="libgphoto2_rules_end"
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

```
Here's where I found it:

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532/comments/26](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532/comments/26)

I don't remember if I restarted udev after editing that file. Couldn't hurt:

sudo /etc/init.d/udev restart

---

### Post by geovino on 2007-03-21
I don't understand. Can you simplify? Otherwise I'll use my other pc with ubuntu that works with out all this trouble.

Why doesn't the camera show up like another hdd? In every other pc my camera turns up as a another sda or hda drive that is mounted and accessed to see the files. That is the best way to handle a digital camera. it's universal and you don't need any special program to open it. How can you mount the drive to see the camera?

---

### Post by fragos on 2007-03-21
The first time a camera is detected you'll get a pop up saying get photographs or ignore.  There's also a check box to tell the system to always use the choice you make this time.  Get photograph's is pretty obvious.  Ignore is a little abstract because it means to mount the camera's memory card as a storage device.  System-> Preferences-> "Removable Drives and Media"-> Cameras tab controls what application will be run after the opo up mentioned above.  In my case I changed it to /usr/bin/f-spot-import.  These tabs perform the same configuration for othe removable devices -- basically USB and CD/DVD.

---

### Post by geovino on 2007-03-22
it doesn't show my camera as another drive. how can I get to see it? this is a very strange problem that hasn't happened with any other distro. How can I solve this problem? 

Thanks

---

### Post by llamakc on 2007-03-22
> **geovino said:**
> it doesn't show my camera as another drive. how can I get to see it? this is a very strange problem that hasn't happened with any other distro. How can I solve this problem? 

Thanks

Have you edited the file with the change I recommended?

---

### Post by fragos on 2007-03-22
In some instances you may need to look at the Nautilus Computer display or withing the Places drop down to see the device.  There are configuration parameters for device visibility but you may have to use the Configuration Editor to seee them.

---

### Post by geovino on 2007-03-23
> **llamakc said:**
> I ran into this problem also. 

Here's what worked for me (something I found off of launchpad)

I edited the /etc/udev/rules.d/45-libgphoto2.rules file, commenting out the 3rd line below, and adding in the fourth one.

```

# udev rules file for libgphoto2 devices (udev < 0.98)
#
#BUS!="usb*", GOTO="libgphoto2_rules_end"
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

```
Here's where I found it:

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532/comments/26](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532/comments/26)

I don't remember if I restarted udev after editing that file. Couldn't hurt:

sudo /etc/init.d/udev restart

How do I edit this and save it?

here's mine:

# udev rules file for libgphoto2 devices (udev < 0.98)
#
BUS!="usb*", GOTO="libgphoto2_rules_end"
ACTION!="add", GOTO="libgphoto2_rules_end"

---

### Post by geovino on 2007-03-23
> **fragos said:**
> In some instances you may need to look at the Nautilus Computer display or withing the Places drop down to see the device.  There are configuration parameters for device visibility but you may have to use the Configuration Editor to seee them.

Where is that is config manager?  Whe I go into my files I see two icons for floppy disk and I don't have a floppy disc. Why is the mounting of drives such a problem in Ubuntu? other distros I've used show the drives with out this trouble!

---

### Post by laidback on 2007-03-23
I have a book called Beginning Ubuntu Linux whch suggests you use gThumb ( Applications>Graphic). 
Once loaded choose File>Import.
The first time you use this program you'll need to setup your camera, so click the Camera Icon on the splash and from the Camera Model dialogue select your model. (It appears that your exact model isn't there so choose the nearest one, A520 I believe) The Port field should then be filled in automatically. 
Close the Import Dialogue box, then open it again, this time your camera should be recognised and thumbnails of your phots displayed.
Select what you want to import, click Import button and the pictures should transfer to you PC. They'll be in /home in a dir formed from date and time.

I've only ever used an Olympus, with that I can see the files as if they are on a memory stick, so have used my browser.

---

### Post by llamakc on 2007-03-23
> **geovino said:**
> I have a Canon powershot A530. When I plug it in to the usb cord to download to my hdd I get this error message:

An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.

Do I have to mount this device ahead of time?

The OP's problem is because of a bug. I've posted a workaround that seems to help many, myself included.

---

### Post by geovino on 2007-03-23
> **llamakc said:**
> I ran into this problem also. 

Here's what worked for me (something I found off of launchpad)

I edited the /etc/udev/rules.d/45-libgphoto2.rules file, commenting out the 3rd line below, and adding in the fourth one.

```

# udev rules file for libgphoto2 devices (udev < 0.98)
#
#BUS!="usb*", GOTO="libgphoto2_rules_end"
SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"

```
Here's where I found it:

[https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532/comments/26](https://launchpad.net/ubuntu/+source/libgphoto2/+bug/67532/comments/26)

I don't remember if I restarted udev after editing that file. Couldn't hurt:

sudo /etc/init.d/udev restart

It works! I did $sudo gedit and it fixed the bug! Thanks :)

---

### Post by llamakc on 2007-03-23
Open a Terminal and type:


 sudo gedit /etc/udev/rules.d/45-libgphoto2.rules
 

Comment out the third line and add insert DIRECTLY beneath it this:
 

SUBSYSTEM!="usb_device", GOTO="libgphoto2_rules_end"
 

Save the file and close Gedit.
 

When you’re done editing the first five lines should look like:
 

# udev rules file for libgphoto2 devices (udev < 0.98)
#
#BUS!=”usb*”, GOTO=”libgphoto2_rules_end”
SUBSYSTEM!=”usb_device”, GOTO=”libgphoto2_rules_end”
ACTION!=”add”, GOTO=”libgphoto2_rules_end”

 

Now, restart udev:
 

sudo /etc/init.d/udev restart


That worked for me.

---

### Post by fragos on 2007-03-23
gksudo gedit

---

### Post by nelso on 2007-03-24
Thanks llamakc, that fixed it for me.

My recollection however, like others, is that with previous versions of The Brown One that my Canon A40 would just fire up and away you would go.

I like new features in software but (heads up to Ubuntu developers) make sure it still works like it used to first.

Maybe it's my age, but I want the Ubuntu developers to SLOW DOWN..., MAKE THE SIMPLE THINGS WORK PROPERLY..., and market share will come. Then we can all sit back and remind our friends and workmates that "I told you so..."

I have just spent a weekend with OS X Tiger and I tell you what, if it wasn't for the fact that you have to pay for the fruit, I'd be there in a flash...

Cheers

Nelso from Australia

---

### Post by geovino on 2007-04-07
two week after I fixed this problem... it came back because I probably upgraded that file since and it changed it back to where it gave me an error message.
I just went in and added that line again but it still didn't work. do I have to reboot? run another command to make it work?

I hope aFeisty upgrade will  fix this problem...

---

### Post by geovino on 2007-04-07
I was able this time to change the file again. Problem solved again.

---

