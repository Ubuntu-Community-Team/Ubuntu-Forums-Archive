---
title: "Howto make config changes?"
date: 2005-10-04
forum: General Help
---

### Post by fragman204 on 2005-10-04
Hi, I'm new to linux so please take easy with me.

I'm trying to make this command to work at starup. (hdpram -d1 -X66 /dev/hdc)
I need to give this command all the before I play any DVD or I get a choppy playback.

All I need is someone to point me in the right direction.

Thanks

---

### Post by SilentCacophony on 2005-10-04
There is a writeup on that in the unofficial ubuntuguide under [How to speed up CD/DVD-ROM?]("http://www.ubuntuguide.org/#speedupcddvdrom"). I'm not too sure about the -X option; I don't think most people use that.

You can **sudo nano /etc/hdparm.conf** to edit the file to make that change at boot time. Looking at the keywords in the commented block in that file, looks like you'd add this to the end:

```
/dev/hdc {
       dma = on
       transfer_mode = 66
}
```

Then save and exit (ctrl-o, return, ctrl-x.)

---

### Post by fragman204 on 2005-10-04
Thank you Silent
I try it, but I still have the same hip hop.
I went back to unofficial unbutuguide and compare the instruction you give my with the guide. Well I made the nano and the gedit equal. The same changes to both and it works.

Thank you again

---

### Post by SilentCacophony on 2005-10-04
Have you tried it without the -X option before (hdpram -d1 /dev/hdc)? Most drives don't need that, and -X66 doesn't look quite right to me, though I've never used that option myself. That corresponds to the *transfer_mode* key in the config file.

Also, just to clarify, any changes to */etc/hdparm.conf* will not take effect until a reboot.

---

