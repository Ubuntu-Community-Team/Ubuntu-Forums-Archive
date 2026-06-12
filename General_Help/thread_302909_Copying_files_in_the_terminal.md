---
title: "Copying files in the terminal"
date: 2006-11-19
forum: General Help
---

### Post by FrozenPixel on 2006-11-19
I'm wanting to know how one would copy a file from my system to a floppy disc. I was thinking it would be similar to a windows DOS command but no luck.

I tried to execute:

cp /etc/dhcp3/dhcpd.conf a:/

but that failed. I'm unclear how to address the floppy under the terminal.

Thanks

---

### Post by jonno73 on 2006-11-19
The floppy drive is mounted at /media/floppy0 

To copy your file you need to do the following.

cp /etc/dhcpd.conf /media/floppy0

---

### Post by aNt1X on 2006-11-19
Basically, it's the "a:/" to be wrong.
The floppy disk is mounted (or has to be mounted) to a directory, something like "/mnt/floppy", and then you can copy the file to that directory.

Look at this guide, it is well explained.

[http://www.alwanza.com/howto/linux/floppy.html](http://www.alwanza.com/howto/linux/floppy.html)

aNt1X

---

### Post by FrozenPixel on 2006-11-19
Thank you both aNt1X and jonno73 for such a quick reply. I had just found the command fstab and wondered after executing it if that was it's name or path.

The command cp /etc/dhcp3/dhcpd.conf /media/floppy0 only copied the file to that path and not to the floppy itself. I will go read that link you provided.

Thanks again.

---

### Post by FrozenPixel on 2006-11-19
Got it to work....:)

---

