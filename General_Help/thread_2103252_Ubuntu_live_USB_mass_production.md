---
title: "Ubuntu live USB mass production"
date: 2013-01-09
forum: General Help
---

### Post by zero2xiii on 2013-01-09
Hay all,

**First of to the moderators. I have no idea where to post this thread so I am posting in general help. Please move to apropriate location if this is incorrect.**

I have a somewhat complicated, yet very easy series of questions. Google, my bestest friend failed me on this one :(.

I want to give workshops to some matric students giving them some very basic tools and guidelines to the computer required market here in south africa. Here is the basic concept with out lines then follows the questions.

I want to ask a minimal entry fee to these workshops to just cover the hardware costs. So I want to keep things minimal to give the most kids possible access to these workshops. The idea being:

A live ubuntu installation on a flash drive (such as a 4GB which is easily and cheaply available in my location, more so than 8GB drives, but if it is a MUST they will be the way to go) from which they can boot and follow the steps I show them. It keeps everything foolproof, except in the RARE case where a usb will not boot from the laptop.

Now this is easy. But here comes the catch parts (in my opinion).
I want to have some extra software on the liveUSB including but not limited to:
Libre Office
Inscape
Gimp
synfig studio
Some (free) codex.
Etc.

Now I realize I can just pop in a USB and run "startup disc creator" and create a bootable flash with persistence. However I am not willing to then boot into each of the (at least) 40 usb drives, install all the software by hand and check that it is working and set everything up by hand. (also having some custom graphics and wallpapers and so will also be nice :), maybe even doing an OEM install so on first boot they can choose their username and password)

I would love to make the process as efficient as possible. Preferable create ONE drive I can then "clone" to the rest. I have considered using "dd" to make the image from the one "finished drive" and then just clone that onto the other with dd again. This might be a slow process, but i assume it will have issues and problems since the UUID and related info will be different from one drive to the next, also no two drives are EXACTLY the same size, so the blocks count might differ by just one, and then dd will freak out most probably.

I have made a custom ubuntu ISO a while back (from a brand new 11.10 a few weeks after it came out) with remastersys if I recall correctly from within a virtual machine.

Tedious process but it functioned.

If at all possible I would like to have both a 32bit and 64bit variant on the drive (disregard the size for a moment) with a check included by the GRUB to check whether or not the system will function with a 64bit version. Basicly a hardware check, with a check if the computer has 2GB or more RAM. Since I found 12.04 (which I plan on basing this off of) to be a bit sluggish on a system with only 1gig ram with a 64bit install.


So to some of the more technical geniuses out there. How will I go about doing this? Any major thoughts or remarks (for one I think like sticking to 32bit and play it 'safe').8-[:?

Kind regards

---

### Post by rmil on 2013-01-09
Generally in this situation I would stick with 32bit only  because you woud not gain so much  more speed and power with USB stick (depending on USB  Faster USBs are more expensive).  If you play with 64 bit you might have problem with missing libraries or something else for which you need intervention in terminal.

You can make custom UUID with tune2fs command or changing of UUID in /etc/fstab or /boot/grub/grub.cfg which you can do with "sed -i" command after copying.

Instead of dd you can use also rsync, grub-install, sed to complete operation because any linux can be copied to other disk.

---

### Post by Cheesemill on 2013-01-09
+1 for using Remastersys for the initial creation of your USB drive.

I don't think you will have problems using dd to mass-produce the drives. As dd works at the block level instead of the file level none of the partition UUID's will be changed. As long as your source image is smaller than the drives you're cloning it onto then you shouldn't have any issues.

---

### Post by C.S.Cameron on 2013-01-09
Another  +1 for Remastersys, It now works for 12.04.
Just set up the system how you want it first. (Libre Office comes pre-installed).

Dd will clone your drives but takes a while to do the job.

You may want to make the drives persistent so work can be saved.
You can make the drives like new by replacing the casper-rw file with an empty one.

You can also remove the Try/Install screen by using the method on this page:

[http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit](http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit)

---

### Post by zero2xiii on 2013-01-10
Hay all,

> Generally in this situation I would stick with 32bit only because you woud not gain so much more speed and power with USB stick (depending on USB Faster USBs are more expensive). If you play with 64 bit you might have problem with missing libraries or something else for which you need intervention in terminal.

Yes I agree with this statement and I think I will be sticking to a 32bit system then. Playing it safe for the crowd.

> Instead of dd you can use also rsync, grub-install, sed to complete operation because any linux can be copied to other disk.

This might an option, but scripting and troubleshooting this might might take longer than just doing it by hand. I am not nearly good enough with scripting, albeit I will keep this in mind for in case it does become a feasible option.

> +1 for using Remastersys for the initial creation of your USB drive.

 I don't think you will have problems using dd to mass-produce the drives. As dd works at the block level instead of the file level none of the partition UUID's will be changed. As long as your source image is smaller than the drives you're cloning it onto then you shouldn't have any issues.

Seems like remastersys is the winner so far. The UUID problem I reffere to are the UUID's used inside the config files esp for GRUB to work. Thus just cloning one drive to another will still have the same UUID references as the original, but its own UUID will be different.

> You may want to make the drives persistent so work can be saved.
 You can make the drives like new by replacing the casper-rw file with an empty one.

 You can also remove the Try/Install screen by using the method on this page:

[http://askubuntu.com/questions/47522.../239368#239368](http://askubuntu.com/questions/47522.../239368#239368)

Thanks for the try install screen tip :D.. (albeit can you please check your direct link for the people that MIGHT reference this thread, as it is broken)


However you lost me with the persistence part. If I create an image with remastersys, and then "install" it onto the USB drives with "Startup disk creator" and select all the free space to be persistence storage, will this work? Or should I replace the casper-rw file still with an empty one after creating the image, or after creating the USB.

Also, it is worth mentioning the attendees will keep the USB's. So I do not need a system which can be "reset" after every boot.

Thanks for all the replies so far guys (and gals, if there are any ;P)

---

### Post by Cheesemill on 2013-01-10
> **zero2xiii said:**
> The UUID problem I reffere to are the UUID's used inside the config files esp for GRUB to work. Thus just cloning one drive to another will still have the same UUID references as the original, but its own UUID will be different.

No it won't.

Cloning a drive using dd will produce an ***exact*** copy. The partition UUID's on the copy will be identical to that of the original.

---

### Post by zero2xiii on 2013-01-10
> **Cheesemill said:**
> No it won't.

Cloning a drive using dd will produce an ***exact*** copy. The partition UUID's on the copy will be identical to that of the original.

I was not aware of this.. Wow.. Proper program :) thanks for the info CHeesemill :D

---

### Post by C.S.Cameron on 2013-01-10
> **Cheesemill said:**
> No it won't.

Cloning a drive using dd will produce an ***exact*** copy. The partition UUID's on the copy will be identical to that of the original.

I have found that a cloned drive's UUID had a (*) added to it.

---

### Post by C.S.Cameron on 2013-01-10
> **zero2xiii said:**
> 
Thanks for the try install screen tip :D.. (albeit can you please check your direct link for the people that MIGHT reference this thread, as it is broken)


However you lost me with the persistence part. If I create an image with remastersys, and then "install" it onto the USB drives with "Startup disk creator" and select all the free space to be persistence storage, will this work? Or should I replace the casper-rw file still with an empty one after creating the image, or after creating the USB.

Also, it is worth mentioning the attendees will keep the USB's. So I do not need a system which can be "reset" after every boot.
 ;P)

I have updated the url in post above, thanks.

What you outline will work. No need to replace casper-rw if they are keeping the drives.

---

### Post by zero2xiii on 2013-01-11
Awsome!

Thanks a lot you guys. Marking this thread as solved.

I will be using remastersys to create the image for the project and then copy that to all the drives from there. Using 10.04 32bit as the base system since it has a rather similar GUI to windows and a lower hardware requirement than 12.04

Appreciate all the input :)

---

