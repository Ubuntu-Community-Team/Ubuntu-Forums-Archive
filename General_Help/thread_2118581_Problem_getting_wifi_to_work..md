---
title: "Problem getting wifi to work."
date: 2013-02-21
forum: General Help
---

### Post by richyw on 2013-02-21
Hi, I have gotten ubuntu 12.10 running on my retina macbook pro. I followed this guide

[http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/)

but am having a big problem in step 4. I have done the first two steps but have a problem when I try to do the third step. I get the error "cannot open: No such file or directory" but i'm pretty sure it is there. Can someone please explain to me what I should do? I'm so close to having ubuntu running again after 6 months of osx!

---

### Post by grahammechanical on 2013-02-21
Oops, missed read your post. Had to edit my post. Let us go over the steps

Step 4 Install WiFi drivers

> 1. sudo apt-get update && sudo apt-get install b43-fwcutter
2. Download driver from: [http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2](http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2)
3. tar -xf broadcom-wl-5.100.138.tar.bz2
4. sudo b43-fwcutter -w /lib/firmware broadcom-wl-5.100.138/linux/wl_apsta.o
5. Reboot and the wireless should work.

What is the problem with step 3? You do not know what to do with tar -xf broadcom-wl-5.100.138.tar.bz2? I am not surprised because the author assumes that you know.

It is my guess is that you run it as a command in the terminal. From this link I would say that tar is a command.

[http://linuxbasiccommands.wordpress.com/2008/04/04/linux-tar-command/]("http://linuxbasiccommands.wordpress.com/2008/04/04/linux-tar-command/")

So copy and paste this into a terminal. You might need to cd (change directory) into the directory where you downloaded the tar.bz2 file to.Or copy it from the Downloads folder into the home folder.

```
cd Downloads
```

and then

```
ls
```

will show you file file in the Downloads directory. Then 

```
tar -xf broadcom-wl-5.100.138.tar.bz2
```

and then move on to step 4.

Regards.

---

### Post by richyw on 2013-02-21
thank you! I actually was in the downloads directory and it wasn't working so I moved it to home and it worked time.  I actually just crashed my computer trying to get the graphics working and reinstalled and now it works in downloads. maybe I spelled "downloads" wrong. 

anyways, I've got a working machine now! now I can get my schoolwork done! hoping that the next version of ubuntu has something for this high-res screen!

ps how do I mark as "solved"?

---

