---
title: "getting ipod to work with banshee on edgy"
date: 2007-01-01
forum: General Help
---

### Post by basvg on 2007-01-01
Hi all,

I recently got myself a nice ipod nano 4gb toy. I read the posts on this forum, went to a windows box to format it properly and put some music on it. After upgrading to Edgy this morning and some fiddling I got to the point where 'ipod --list' actually shows my ipod. Good start. 

I fired up banshee but no ipod showed up. My second attempt was to try gtkpod, which does work. I'm not too happy with the interface though, so decided to investigate further. A buddy pointed me to automatix2 where I installed ilife (which also includes banshee). No luck there either.

Now I'm at a loss.. can anyone help out?

  Bas

---

### Post by scoon on 2007-01-01
Hey there, 

See if this helps you out: [http://bugzilla.gnome.org/show_bug.cgi?id=347960]("http://bugzilla.gnome.org/show_bug.cgi?id=347960")

The other thing to try would be to start banshee from a term window and see if any error messages get displayed.

-scoon

---

### Post by basvg on 2007-01-01
Thanks for the link... unfortunately it didn't help me :( Also there doesn't seem to be much useful info on the terminal:

```
bas@Librarian { ~ }$ banshee 
Warning: [1/1/2007 4:05:09 PM] (Cannot connect to NetworkManager) - An available, working network connection will be assumed

(/usr/lib/banshee/banshee.exe:23457): GLib-GObject-WARNING **: value "128" of type `gint' is invalid or out of range for property `bitrate' of type `gint'
Debug: [1/1/2007 4:05:11 PM] (Default player engine) - GStreamer 0.10
Debug: [1/1/2007 4:05:11 PM] (Audio CD Core Initialized) - 
Warning: [1/1/2007 4:05:11 PM] (Could not initialize plugin `Daap') - Daemon not running
Setting MusicBrainz proxy to www.musicbrainz.org:80
```

---

### Post by scoon on 2007-01-01
Hey there, 

When you plug in your ipod, what does dmesg show about it?

-scoon

---

### Post by basvg on 2007-01-01
when I check /var/log/messages then I see:
```
Jan  1 18:10:22 Librarian kernel: [17199685.524000] usb 4-5: new high speed USB device using ehci_hcd and address 10
Jan  1 18:10:22 Librarian kernel: [17199685.668000] usb 4-5: configuration #1 chosen from 2 choices
Jan  1 18:10:22 Librarian kernel: [17199685.668000] scsi6 : SCSI emulation for USB Mass Storage devices
Jan  1 18:10:27 Librarian kernel: [17199690.672000]   Vendor: Apple     Model: iPod              Rev: 1.62
Jan  1 18:10:27 Librarian kernel: [17199690.672000]   Type:   Direct-Access                      ANSI SCSI revision: 00
Jan  1 18:10:27 Librarian kernel: [17199690.676000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)
Jan  1 18:10:27 Librarian kernel: [17199690.676000] sda: Write Protect is off
Jan  1 18:10:27 Librarian kernel: [17199690.680000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)
Jan  1 18:10:27 Librarian kernel: [17199690.680000] sda: Write Protect is off
Jan  1 18:10:27 Librarian kernel: [17199690.680000]  sda: sda1 sda2
Jan  1 18:10:27 Librarian kernel: [17199690.684000] sd 6:0:0:0: Attached scsi removable disk sda
Jan  1 18:10:27 Librarian kernel: [17199690.684000] sd 6:0:0:0: Attached scsi generic sg0 type 0
```
This told me that the device is located at sda... after updating /etc/fstab I was able to manually mount the ipod..

---

### Post by scoon on 2007-01-01
Hey there, 

And did that solve your problem?

-scoon

---

### Post by basvg on 2007-01-01
Errrr... nope. As I wrote in the original post: I can mount the device, no problem. Banshee doesn't see the ipod, whether it is mounted or not

---

