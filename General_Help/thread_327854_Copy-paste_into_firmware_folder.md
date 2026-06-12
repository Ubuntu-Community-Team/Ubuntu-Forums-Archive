---
title: "Copy-paste into firmware folder"
date: 2006-12-29
forum: General Help
---

### Post by gobuntu on 2006-12-29
In needing to copy-paste from usb-stick the driver bcmwl5.sys to the /lib/firmware folder.

I have issued sudo -i from a terminal prior to that, but the Paste option appears dim when I open the target folder. However, I can paste easily into the usb-stick, where the result is a copy right next to the original

Why not possible?

How to overcome it?

Thanks.

---

### Post by 23meg on 2006-12-29
Start Nautilus as root to temporarily have write access to folders outside your home folder.```
gksudo nautilus
```

---

### Post by gobuntu on 2006-12-30
Thanks 23meg,

Did what you said, but got this message back: (abbreviated)
------------------------------
WARNING while connecting to session manager. Authentication rejected,
reason: None of the authentiation protocol specified are supported and host-base
authentication failed.

(nautilus: 4957) libgnomevfs-WARNING failed to open session DBUS connection. Did not
receive reply. Possible causes include: the remote application did not send a reply, the
message bus security policy blocked the reply, the rep volume monitoring will not work.
---------------------------------

Still went ahead and tried to cut and paste, and no difference.


Any further help will be appreciated.

---

### Post by 23meg on 2006-12-30
Just hit Alt+F2, type ```
gksudo nautilus
``` and you should have write access to your /lib folder in the instance of Nautilus that's running as root. Make sure you copy and paste the file with that instance.

---

### Post by gobuntu on 2006-12-30
Thanks 23meg,

It now worked.

Now will go onto the next steps on making the BROADCOM wireless work.

Will post separate message if so needed.

:D

---

### Post by 23meg on 2006-12-30
Good to know; start a new thread with an appropriate title if you have more problems.

---

### Post by 00Luke on 2007-02-12
> and you should have write access to your /lib folder in the instance of Nautilus that's running as root. Make sure you copy and paste the file with that instance

I've tried to do this, but don't understand the bit about "Make sure you copy and paste the file with that instance" - What am I meant to be doing? Can I use Thunar to copy and paste the files once I've done the Alt+F2 --> gksudo nautilus ? 

Any help would be greatly appreciated - I'm trying to get my wireless USB stick working too. Thanks!

---

### Post by jocko on 2007-02-12
> **00Luke said:**
> I've tried to do this, but don't understand the bit about "Make sure you copy and paste the file with that instance" - What am I meant to be doing? Can I use Thunar to copy and paste the files once I've done the Alt+F2 --> gksudo nautilus ? 

Any help would be greatly appreciated - I'm trying to get my wireless USB stick working too. Thanks!

Thunar? That's the xubuntu file manager? I don't think xubuntu has gksu or nautilus, those are specific to gnome as far as I know. But to open thunar with root permissions, I think you can run "sudo thunar" from a terminal.

---

### Post by 00Luke on 2007-02-12
Ah fantastic - thank you very much! Although now I still don't understand how I use my wireless USB stick? If I've copied the files into the /firmware folder, how do I install the USB stick? Or should it just recognise it?

I'm very new to all this, just trying to get my laptop running on Xubuntu, so thanks for your help - sorry for being rubbish :)

---

