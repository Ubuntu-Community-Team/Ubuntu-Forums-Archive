---
title: "bootsplash and grub theme (matrix-splash)"
date: 2007-08-03
forum: General Help
---

### Post by guttersnipe on 2007-08-03
I'm trying to customize my laptop to a complete matrix theme.

Dark green everything with moochrome #00FF00 (green) text? Check.
Customized login sound to be "Welcome to the desert of the real"? Check.
xwinwrap glmatrix background? Check.
kick-*** grub theme? Nope.
kick-*** bootsplash? Nope.

Here's the deal, someone developed a kick-*** set of boot screens for grub, bootsplash, and kdm (I have gdm, so I'm not even going to bother with this latter). The project's name is "matrix-splash" and can be accessed from here: [http://www.kde-look.org/content/show.php?content=27889&forumpage=3&PHPSESSID=cae](http://www.kde-look.org/content/show.php?content=27889&forumpage=3&PHPSESSID=cae) . 

Here's the files:
```

guttersnipe@trinity:~/matrix-splash$ ls -R
.:
Bootsplash_theme  grub_theme  License  splash-kde_theme

./Bootsplash_theme:
config  images

./Bootsplash_theme/config:
bootsplash-1024x768.cfg  bootsplash-1280x1024.cfg  bootsplash-800x600.cfg

./Bootsplash_theme/images:
bootsplash-1024x768.jpg   bootsplash-800x600.jpg  silent-1280x1024.jpg
bootsplash-1280x1024.jpg  silent-1024x768.jpg     silent-800x600.jpg

./grub_theme:
message
...

```

The instructions on the link above are for SUSE.  The grub theme only has a file called message.  You're supposed to backup the already existing /boot/grub/message file (which does not exist), and somehow--my best guess is magic--grub turns this file into an image and gives you an awesome picture on boot.  Not on my machine.  Not in Ubuntu.  If you read the comments, you'll see several unanswered cries-for-help from ubuntu users.

I did some searching.  While there's nothing specific to matrix-splash, I came across [this]("http://doc.gwos.org/index.php/GfxBoot").  Apparently, it's something native in SUSE that can be preformed in Ubuntu with gfxboot.  I followed the instructions to the tee.  Nothing.  I then went back a few dozen times and tried varying their instructions.  Nothing.  I gave up, that's why I'm here.  Is there any way to convert that bloody "message" file to something that ubuntu understands natively?

----

Then there's the bootsplash.  Look at the directory structure again.  I've got a folder called config with .cfg files in it, and a folder called jpg with .jpg files in it.  Everything I've read about customizing the bootsplash in ubuntu calls for .so files. :confused::confused::confused: I didn't even know where to start.  Any ideas?

Thanks in advance.

---

### Post by upthelum on 2007-08-03
For your themes when you are adding them, browse to the downloaded file - presumably a .tar.gz extension - and select it, which should install it.
Hope this helps...

---

### Post by guttersnipe on 2007-08-10
> **upthelum said:**
> For your themes when you are adding them, browse to the downloaded file - presumably a .tar.gz extension - and select it, which should install it.
Hope this helps...

I don't quite understand your solution.

The problem is that I DON'T HAVE a .tar.gz file.  All I have is a images and config directory...

I could TRY compressing the two directories into a .tar.gz file, but I highly doubt single-clicking on it will install it for me :-D.  Can you elaborate on just what "select" means?

---

### Post by cjm5229 on 2007-08-12
Try getdeb.net There is an application called Startup Manager, It is a Deb file so all you have to do is click on the file after you download it and click install. It will let you set your Usplash and grub background. Also if you look at Gnomelook instead of KDElook You might find that theme for Gnome.

---

