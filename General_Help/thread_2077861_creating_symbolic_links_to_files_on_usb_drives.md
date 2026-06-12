---
title: "creating symbolic links to files on usb drives"
date: 2012-10-29
forum: General Help
---

### Post by DonTommy on 2012-10-29
Hey
I got an ubuntu server set up, which automounts a couple of external usb harddrives.

Now I wanna make a folder which links every file from certain folders on the usb drives to that special folder, is that possible?

I tryed doing a "sudo ln -s /media/usb0/photos/*" and I typed that when I was in the folder where I wanted the links, but it told could not create symbolic link, the file exists? (translated error msg from danish to english)

Thanks

---

### Post by drmrgd on 2012-10-29
The correct syntax for 'ln' is ln -s TARGET LINK_NAME where TARGET is the location you want the link to point to, and the LINK_NAME is the name of the link you want.  I don't believe that you can glob that (i.e. use *).  But, if you want to create a symbolic link to that photos directory from (let's say) your home directory:

```
ln -s /media/usb0/photos/ /home/<username>/PhotosOnUSB0
```

That will create a link in your home folder (substitute <username> with your actual username!) that's called "PhotosOnUSB0" that points to the photos folder on usb0.

Hope that helps!

---

### Post by DonTommy on 2012-10-29
It helps a little ;)

What I want to do is that i have these usb drives connected with a photos folder on both of them, I want them somehow merged into one folder, without moving the files into the same harddrives or anything, so I can browse trough them all without changing folders, like a fake folder or something with all the photos from both harddrives in it. Is that even possible?

Thanks

---

### Post by drmrgd on 2012-10-29
Hmmmm...I'm not sure how you can point to two locations with one link.  I don't think it's possible.

---

### Post by DonTommy on 2012-10-29
Crap... thanks for your time though, and ill be happy to listen if you or anyone else can figure out how it can be done :)

---

### Post by COMECON on 2012-10-29
You could create a symbolic link for each file on both drivers you want to link, but it's so... tedious. You can't create a symbolic link pointing to two different places, that'd be like if you made a shortcut on your desktop pointing to *~/Images* and *~/Documents*!
So I recommend you creating a folder and then just two subfolders:
```
$ mkdir ~/usbhub
$ ln -s /media/usb0/photos/ ~/usbhub/usb1
$ ln -s /media/usb1/photos/ ~/usbhub/usb2
```Just in example.

---

### Post by LewisTM on 2012-10-29
You can create a merged view of folders with UnionFS or Aufs. Both can be awfully complicated to setup and I have no experience with them, but in theory it should work. 

Aufs needs package **aufs-tools**

Syntax:
```
sudo mount -t aufs -o br:**/dir1**:**/dir2** none** /mergedir**
```

Two useful links:
[Forum thread]("http://ubuntuforums.org/showthread.php?t=1179333")
[Aufs man page]("http://manpages.ubuntu.com/manpages/precise/man5/aufs.5.html")

Cheers!

---

