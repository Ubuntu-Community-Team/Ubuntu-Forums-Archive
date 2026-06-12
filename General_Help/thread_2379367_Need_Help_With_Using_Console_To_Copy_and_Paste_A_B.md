---
title: "Need Help With Using Console To Copy and Paste A Bunch of Files"
date: 2017-12-04
forum: General Help
---

### Post by DeadlyOats on 2017-12-04
EDIT:  I corrected the path.   /usr/share/backgrounds to  /usr/share/wallpapers.  I copied the wrong path and pasted it as I typed the original request.  That's because they moved the wallpapers from .local in your home folder in Kubuntu 16.04 to the share folder in /root/usr in Kubuntu 17.10, and I was searching the forums for info on where they moved it to.

Original post begins, below.

I want to copy a bunch of wallpapers from my external USB Hard drive to /usr/share/wallpapers in my Kubuntu 17.10 installation.  I tried to copy the images from my USB drive and then paste them to /usr/share/wallpapers, but I don't have permissions....

It took me awhile to remember that as user, I don't have access to all of the folders in the system...  I don't want to permanently change any permissions, but I'd like temporary permission to copy all of those files.  There are 37 .jpg files and two .txt files.  I want to copy the .jpg files only, and paste them to /usr/share/wallpapers.

So, what would I have to type in console to copy all of those files from my USB drive and paste them to /usr/share/wallpapers in my Kubuntu 17.10 installation?

Thanks in advance.

---

### Post by Kirk Schnable on 2017-12-05
sudo cp /path/to/your/usb/*.jpg /usr/share/wallpapers/

---

### Post by DeadlyOats on 2017-12-05
I had to hunt around to find the path to my usb...  I used the lsblk command and found that the path to my usb is

> /media/myusername/Nameof Usbdrive.

So, when I used the command you showed me, this is what I used:

> "sudo cp /media/myusername/Nameof Usbdrive/wallpapers/*jpg /usr/share/wallpapers"

The output I get is:

> "cp: cannot stat '/media/myusername/Nameof': No such file or directory"  
"cp: cannot stat 'Usbdrive/wallpapers/*.jpg': No such file or directory"

So, I think that Kubuntu thinks that "Nameof Usbdrive" is two different directories.

In Dolphin file manager, I right click on "Nameof Usbdrive" and I get it's label and it's path as shown by lsblk.  I tried editing it's label to add an underscore, "Nameof_Usbdrive."  But that did not change the name of the drive, nor did it change it's path, even after un-mounting and re-mounting the drive.  The name returned with lsblk remained "Nameof Usbdrive."

How do I fix this problem?  Dolphin displays the drive, and its contents with no issue, but using your command with the path that lsblk is showing me, I get the error message as illustrated above.

---

### Post by Kirk Schnable on 2017-12-05
Yeah, that's happening because of the space in the directory.  What you have to do in that case is escape the space with a slash like so.

"Nameof\ Usbdrive"

---

### Post by howefield on 2017-12-05
Try using the tab autocomplete when typing the path....

In your example above "*/media/myusername/Nameof Usbdrive. *" there is a space, you would need to escape the space or otherwise eliminate it.

---

### Post by DeadlyOats on 2017-12-05
Thanks, Kirk Schnable!  That fixed it!  At first I did it like this:

"Nameof\Usbdrive"

I got the "cp cannot stat" error message again.  Then I noticed there was a space after the \

"Nameof\ Usbdrive"

Now my wallpapers are copied over.  Thanks, again!

And thank you, too, howefield your your input.  It is much appreciated.

---

### Post by vasa1 on 2017-12-05
You may already know this, but images even in your home folder will be available to set as your wallpaper.

---

### Post by DeadlyOats on 2017-12-05
vasa1, here's an example of sudo in the hands of an expert:

[IMG]https://i2.wp.com/imgs.xkcd.com/comics/sandwich.png[/IMG]

I only wish I was that good with it.  LOL

---

