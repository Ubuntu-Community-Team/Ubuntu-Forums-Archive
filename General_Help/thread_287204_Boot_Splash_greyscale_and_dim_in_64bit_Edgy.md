---
title: "Boot Splash greyscale and dim in 64bit Edgy"
date: 2006-10-28
forum: General Help
---

### Post by wilberfan64 on 2006-10-28
After a wonderfully successful morning installing Edgy on my 32bit box, I've just completed a 64bit Edgy install on my other box.  

I had to download (via Automatix) the NVidia driver, and edit my xorg.conf file to get my desktop to the proper res, but my boot splash screen (which looks pretty damn cool on the 32bit box) is all dim and greyscale.

I added "vga=791" to the menu.lst file--and that DID change the res, but the screen still has no color, etc...

Any thoughts?

---

### Post by fo0b4er on 2006-10-28
I am having the exact same problem on my laptop with xubuntu (32-bit).  I just upgraded to edgy and the new splash screen is dim and greyscale. :???:   If I find a way to fix it I'll post it here.

---

### Post by fo0b4er on 2006-10-28
I found a solution!  It's actually pretty easy. :-D   All you have to do is follow the instructions from #5 to #6A at [https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto). You might also want to read this thread: [http://ubuntuforums.org/showthread.php?t=285366](http://ubuntuforums.org/showthread.php?t=285366), which provides a similar solution.

---

### Post by wilberfan64 on 2006-10-28
Didn't work--unless I did something wrong.

When I ran   > sudo update-alternatives --config usplash-artwork.so


I got this response:

> There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.

My menu.lst is already set up properly...

---

### Post by fo0b4er on 2006-10-28
The command you quoted is correct.  You need the brackets.  The "$(uname -r)" part of the command will get automatically replaced by the name of your kernel image.  Try just the command "uname -r" and you will see what I mean.

---

### Post by wilberfan64 on 2006-10-28
Here's what I got:

> sudo dpkg-reconfigure linux-image-$(uname -r)
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.17-10-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.17-10.33 was configured last, according to dpkg)
Running postinst hook /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Why couldn't it find a splash image?

---

### Post by wilberfan64 on 2006-10-28
Well, this doesn't seem to be working for me...   I've even tried a oouple of different vga settings.   The greyscale image does change size, but I'm not getting a progress bar, etc...
:-k

---

### Post by fo0b4er on 2006-10-28
Do you have usplash-theme-ubuntu installed?  If not, install it.  If it is installed, try re-installing it.  Then run the commands I gave you again.  If that does not work then I don't know what to do...  I'm not an expert or anything, but what I said before worked for me.

EDIT: You don't have to run "sudo update-alternatives --config usplash-artwork.so", that's in step 4!  I said steps 5 to 6A, and don't forget the last part: run the command "sudo update-grub".

---

### Post by wilberfan64 on 2006-10-29
> **fo0b4er said:**
> Do you have usplash-theme-ubuntu installed? 

I have a 'usplash.theme.ubuntu.so' installed.  Is that what you mean?

>   If not, install it.  If it is installed, try re-installing it. 

How would I do that??


>  EDIT: You don't have to run "sudo update-alternatives --config usplash-artwork.so", that's in step 4!  I said steps 5 to 6A, and don't forget the last part: run the command "sudo update-grub".

I guess I was too overeager with the steps (!), but I DID run 'sudo update-grub'...

I appreciate your efforts on my behalf!

---

### Post by fo0b4er on 2006-10-29
It doesn't really matter that you did step 4, so don't worry about it.  I don't mean "usplash.theme.ubuntu.so", I mean the package named "usplash-theme-ubuntu".  You would install it with: ```
sudo apt-get install usplash-theme-ubuntu
```
or re-install it with: ```
sudo apt-get install --reinstall usplash-theme-ubuntu
``` then do step 5: ```
sudo dpkg-reconfigure linux-image-$(uname -r)
``` and the last part of step 6A: ```
sudo update-grub
```

---

### Post by wilberfan64 on 2006-10-29
Hey, I REALLY appreciate you holding my hand like this, and giving me a step-by-step!

But it didn't work...   And, you know, I had a feeling it wouldn't work:

Last night when I did a clean re-install, I noticed that the Live CD boot splash was all grey and yucky.   Maybe there's no connection, but...

It's certainly only a cosmetic problem--and I can probably learn to live with it, but it's interesting that this fixed it for you but not me.

---

### Post by fo0b4er on 2006-10-29
Well then I'm out of ideas...  to bad it didn't work for you.  You could try posting your problem in that other thread I linked to.  That might attract the attention of someone who knows more about this than me.  The problem might even get fixed after some future software update.  Good luck!

---

### Post by peter07 on 2006-10-29
Many users have the same problem, but there is no soultion. Other threads:

[http://ubuntuforums.org/showthread.php?t=286334&highlight=grey+splash](http://ubuntuforums.org/showthread.php?t=286334&highlight=grey+splash)
[http://ubuntuforums.org/showthread.php?t=284064&highlight=grey+splash](http://ubuntuforums.org/showthread.php?t=284064&highlight=grey+splash)

I also have the same problem :(

---

### Post by fo0b4er on 2006-10-29
Have you tried my solution?  It worked perfectly for me.  My bootsplash looks great now! :D

---

### Post by peter07 on 2006-10-29
> **fo0b4er said:**
> Have you tried my solution?  It worked perfectly for me.  My bootsplash looks great now! :D

I have the newest version of usplash-theme-ubuntu (0.6)

What I have tried:
```
sudo apt-get install --reinstall usplash-theme-ubuntu
```
No errors.
```
sudo dpkg-reconfigure linux-image-$(uname -r)
```
ERROR:
```
Searching for splash image ... none found, skipping ...

```
Then I've checked three resolutions ( standard and ...):
```
# defoptions=quiet splash vga=791
```
```
# defoptions=quiet splash vga=788
```
Each time I've ran:
```
sudo update-grub

```
ERROR:
```
Searching for splash image ... none found, skipping ...
```
And the results:
BAD. Ubuntu logo is still black. It was just moved to the right corner. I don't get colors. 

Maybe it's something with amd64 version?

---

### Post by fo0b4er on 2006-10-29
You guys really need an expert here, because I sure am not one.  All of the cases of this I've heard of (except mine...) have been with the amd64 version.  I really don't know why this is...  What happens when you run: ```
sudo update-alternatives --config usplash-artwork.so
```

---

### Post by MintabiePete on 2006-10-29
Thanks  for those easy to read instuctions fo0b4er  :)

---

### Post by fo0b4er on 2006-10-29
No problem MintabiePete! :D  Did my instructions work for you? (I presume you have the same problem since you are reading this thread... ;) )

---

### Post by featherking on 2006-10-29
Just so people know, when you run dpkg-reconfigure on the linux image and it says "Searching for splash image ... none found, skipping ..." that is actually referring to the GRUB splash image. This is normal. Running sudo update-grub will give you the same error.

Having said that, my boot screen is also messed up, it looks like a diagram with numbers and colors and its mostly gray. Have not found a fix yet..

---

### Post by fo0b4er on 2006-10-29
Thanks for that info. :-D  That answers a few of my questions.  Did you try my fix?  Apparently "it should be good for most usplash problems."

---

### Post by wilberfan64 on 2006-10-29
Actually, this may be a known bug.   From [this page]("https://wiki.ubuntu.com/EdgyEft/Beta"):

> On certain platforms with 64-bit CPUs and NVIDIA graphics, the graphical boot screen does not function and a blank screen is displayed. The solution is to wait patiently for the login screen to appear ([WWW] #56587).

That doesn't sound like a *solution* to me!   :rolleyes:

---

### Post by fo0b4er on 2006-10-30
I think maybe that's supposed to be a joke! ;)  (the "wait patiently for the login screen to appear" part) I don't think it's just a problem with "64-bit CPUs and NVIDIA graphics" , because it happened to my computer which runs 32-bit xubuntu and does not have NVIDIA graphics...

---

### Post by anarmyofnone on 2006-10-30
I'm having the same issue also, and have not been able to find a solution yet.  I'm running 64 bit Edgy and I get the Ubuntu logo in black and white with a garbled progress bar. The solutions presented in this thread so far have not fixed the issue. Setting the VGA option in menu.lst does change the resolution, but does not fix the colors.  This isn't an Nvidia issue, because I've got an Ati display adapter.

---

### Post by rcatman on 2006-10-31
I'm having a similar problem.

At the end of 'sudo dpkg-reconfigure linux-image-$(uname -r)' i see this..

```
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

The result is the same when running 'sudo update-grub'
```
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-10-386
Found kernel: /boot/vmlinuz-2.6.15-27-386
Found kernel: /boot/vmlinuz-2.6.15-26-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

I even reinstalled usplash-theme-ubuntu. What is going on!? Does anyone have any ideas?

---

### Post by fo0b4er on 2006-10-31
> **featherking said:**
> Just so people know, when you run dpkg-reconfigure on the linux image and it says "Searching for splash image ... none found, skipping ..." that is actually referring to the GRUB splash image. This is normal. Running sudo update-grub will give you the same error.

Those messages you are getting are not related to the issue you are having.  I think the steps I posted earlier worked for me but not for you guys because we have different problems.  I think my problem was caused by a bad graphics card in an old laptop, while your problems seem to be more of a bug ([this]("https://launchpad.net/distros/ubuntu/+source/usplash/+bug/56587") one?) in 64-bit ubuntu...

---

