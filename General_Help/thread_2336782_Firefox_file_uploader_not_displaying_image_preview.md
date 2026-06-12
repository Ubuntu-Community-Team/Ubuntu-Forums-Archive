---
title: "Firefox file uploader not displaying image previews"
date: 2016-09-11
forum: General Help
---

### Post by goemonburo on 2016-09-11
This cannot possibly be a hard one:  I recently installed Lubuntu 16.04.1 LTS and am using Firefox for Linux 48.0.  In the past, I've always gotten a preview of the file I'm trying to upload (such as a jpg that I want to post on FB) when I click...it's vital so you don't have to remember the filename of each image you want to post or have a second application open that shows the files.

But for some reason, that's not showing up anymore.  If I want to upload a bunch of yesterday's photos to Facebook, I have no way of seeing the images...I just get a list of filenames.  Which if they're in 20160910_123456.jpg, 20160910_123476.jpg format, it's pretty impossible to know if I'm uploading the right file.

Is this a simple setting somewhere in Firefox or my Lubuntu file manager?  I have "show thumbnails" selected in the filemanager and it works fine there.  Just when I'm uploading files to the net that it doesn't work.  

Please help...this is a big frustration!

:-)

Thank you!!!!

---

### Post by goemonburo on 2016-09-11
Update:  this seems to be related to image size!  I can see previews that are less than 5MB, but above that I cannot.  Seems like this HAS to be something I can set, either in Firefox itself or in my system settings???

Scratch that:  Size matters (hah!) but not in all cases.  If I try to upload from my HOME directory, it works on images less than 5MB.  If I try from an attached USB external disk, it fails no matter what.

---

### Post by alexandr-kaprizkin on 2016-09-11
If you go into **Edit > Preferences > Display** of your file manager, and change the value of **Do not generate thumbnails which exceeds the size of xxxx KB **to something larger. Does it work then?

---

### Post by goemonburo on 2016-09-11
No, unfortunately that doesn't seem to be the issue.  I can see the previews in the file manager just fine.  But somehow there seems to be a separate firefox setting that's causing files to not show thumbnails.  Perhaps.

I tried setting the file manager preview size as high as 30000kb and it didn't change anything.

If feel like there's probably an about:config setting in Firefox that I should be able to tweak and fix this.  Nobody knows?

---

### Post by vasa1 on 2016-09-11
What about when you try *File > Open* in Firefox 48 and navigate to a folder with images? Do you get previews in that window pane for images of any size?

---

### Post by goemonburo on 2016-09-11
No, that doesn't give me images either.  Just a list of the files...  :-(

---

### Post by vasa1 on 2016-09-12
> **goemonburo said:**
> No, that doesn't give me images either.  Just a list of the files...  :-(
Can you try with a new profile (support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles) or with all extensions disabled? What happens then?

---

### Post by goemonburo on 2016-09-12
I will try with a new profile...more shortly.  But I did try in Safe mode and the same thing is happening, so I don't think it's related to extensions.  

More when I've made a new profile!  :-)

---

### Post by goemonburo on 2016-09-12
Is it by any chance one of those things where I have to log out (or reboot) before changes appear?  I haven't done that...yet.

---

### Post by vasa1 on 2016-09-12
Restarting Firefox should be enough. No need to log out.

---

### Post by goemonburo on 2016-09-13
Is there possibly an issue with it being local versus "non-local"?  It seems to work if I'm on my home computer if I use the file manager.  I see thumbnail previews.  But not if I'm using a VNC connection which has the folder mounted remotely over sshfs.  Is that the reason?

---

### Post by vasa1 on 2016-09-15
Here's what seems to be a related question at least as far as size goes: [http://askubuntu.com/questions/825271/how-can-i-enable-the-image-preview-for-large-files-in-the-file-choosing-dialog-w](http://askubuntu.com/questions/825271/how-can-i-enable-the-image-preview-for-large-files-in-the-file-choosing-dialog-w)

This maybe more relevant: [Thumbnails in File upload dialog?]("https://forum.xfce.org/viewtopic.php?id=10133"). Reading all the posts there isn't a bad idea.

---

