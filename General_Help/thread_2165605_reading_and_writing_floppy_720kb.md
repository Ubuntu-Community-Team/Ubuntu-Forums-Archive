---
title: "reading and writing floppy 720kb"
date: 2013-08-05
forum: General Help
---

### Post by ottosykora on 2013-08-05
I would like to make a dd from a floppy with 720kb , if possible then write the content to floppy 1.44mb

So far did not even manage to read anything from my usb connected floppy drive.
Is it possible at all?

Or what version of linux , ubuntu should I look for to make this possible?

---

### Post by scbingham on 2013-08-05
If you can see the contents of the floppy, then I don't see why not.

dd if=/media/fd0 (or whatever your floppy is) of=/home/your_user/a_file_name should do it

Then put in 1.4Mb floppy & do

dd if=/home/your_user/a_file_name of=/media/fd0

Try it & see. Good luck.

---

### Post by ajgreeny on 2013-08-05
Your difficulty may be in mounting the floppy, which now will probably require you to use command ```
udisks --mount /dev/fd0
```

See also [http://ubuntuforums.org/showthread.php?t=2164736&p=12742817#post12742817](http://ubuntuforums.org/showthread.php?t=2164736&p=12742817#post12742817) where I discussed this, though there was a problem with the unmounting command.

---

### Post by Dennis N on 2013-08-05
> **ottosykora said:**
> I would like to make a dd from a floppy with 720kb , if possible then write the content to floppy 1.44mb

So far did not even manage to read anything from my usb connected floppy drive.
Is it possible at all?

**Or what version of linux , ubuntu should I look for to make this possible?**

I can't speak to mounting from the command line, but I find that on Xubuntu releases I checked, a TEAC USB floppy drive automounts on insertion only with Xubuntu 13.04. Tested with Xubuntu 12.10 and 12.04 systems, and it's not recognized. Unable to try Ubuntu, but maybe it's the same there.

---

### Post by ottosykora on 2013-08-06
the problem is rather to see the media and to mount it in first place. It seems that the current kernel can not handle this any more

---

### Post by ottosykora on 2013-08-06
well, the answer to the udisks:

otto@LAPTOPOTTOS6:~$ sudo udisks --mount /dev/fd0
[sudo] password for otto: 
Cannot stat device file /dev/fd0: Datei oder Verzeichnis nicht gefunden
otto@LAPTOPOTTOS6:~$



up on insertion the floppy rotates short, but it seems that ubuntu (12.04) finds nothing abt it so far.

Note that it is 720kb floppy and not 1.44mb one! 
Current versions of windows can operate only 1.44mb, therefore I try linux, but it seems no luck either.

So far I am not able to read also normal 1.44mb floppy, the msg is the same

Any other idea?

---

### Post by ottosykora on 2013-08-07
any idea how to mount floppy (usb floppy drive) on 12.04?

---

### Post by SeijiSensei on 2013-08-07
I doubt a USB connected floppy will appear as /dev/fd0.  That only works with floppies connected to the system's hardware.

Try this. Disconnect the USB cable, then open a terminal window and type "sudo tail -f /var/log/syslog".  Now plug the cable back in.  You should see log entries appear that will give you an idea how the device is named.

---

