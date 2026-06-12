---
title: "I think I killed it"
date: 2007-02-22
forum: General Help
---

### Post by band-aid on 2007-02-22
Well, I was feeling brave so I compiled a new kernel using the guide from the master kernel thread. Everything went fine and, as I expected, I needed to reinstall the nvidia drivers. The problem is, I am used to installing the drivers using automatix. After some googling I decided to give the "envy" script a try. This is where everything went to pot. After running the script, I was still unable to start X because apparently the nvidia driver was not installed or something. Well, now I cannot launch using any of my kernels. I have to use recovery mode to be able to do anything. I have spent the last two hours trying to install the drivers manually but have so far been unsuccessful. I REALLY don't want to reformat and reinstall because I've spent a great deal of time getting everything set up just the way I like it. On the bright side, I have had to learn how to associate with a wireless access point using only the terminal. Now I'm not completely dependent on nm-applet. Any help is greatly appreciated.

---

### Post by band-aid on 2007-02-22
bump

---

### Post by Peepsalot on 2007-02-22
My X breaks every time there is a kernel update.  It requires reinstalling the nvidia drivers under the new kernel.  I just get the latest stable one from the nvidia website and use their install method.  I can do it pretty quickly and easily though now that I figured it out.

When you get X error message, use Ctrl-Alt-F2 to get to a fresh console.
Using a text based browser(I think I usually use elinks), go to nvidia.com and download the driver if you don't already have it
The file is packaged as an execultable script.  Just "chmod +x" the file  and run it with sudo.

Reboot and you should be good to go.

---

