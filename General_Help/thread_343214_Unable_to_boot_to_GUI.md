---
title: "Unable to boot to GUI"
date: 2007-01-21
forum: General Help
---

### Post by mgaskell on 2007-01-21
Help!!

I edited out the Synaptics Touchpad line in my /etc/X11/xorg.conf file in an attempt to work around a screwed up Synaptics Touchpad behavior. I can no longer boot to the Edgy gui. I have rebooted to the live CD to try and restore the file to it's original configuration but I don't know how to get to the file with sudo gedit.

I cannot find my hda3 partition. I tried a mount -a. I am new to this and out of ideas. The only thing I did was edit out that line so I am assuming that's what I did wrong.

If I cannot use this live cd boot, what commands do I issue from the non gui command line?

Thanks in advance.

Mike

---

### Post by JamieC on 2007-01-21
Use the rescue to mount your Ubuntu filesystem and run the following command:
```

sudo vim /etc/X11/xorg.conf

```

Fix your errors and then type:
```

startx

```

---

### Post by Tmi on 2007-01-21
> **mgaskell said:**
> I have rebooted to the live CD to try and restore the file to it's original configuration but I don't know how to get to the file with sudo gedit.

You mean you don't know how to edit it? Try "sudo nano /etc/X11/xorg.conf". Not sure if that was what you meant though.

And a good thing to remeber is to always, always, aaaaalways, backup your xorg.conf or other important files before editing them, just in case something goes wrong.

---

### Post by mgaskell on 2007-01-21
Thanks. 

Here I go.

---

