---
title: "Can't 'apt-get update'"
date: 2005-10-16
forum: General Help
---

### Post by Veracon on 2005-10-16
Just a few minutes ago, I tried to update the repositories using apt-get update. It successfully downloaded the sources and packages, but then it gave me an error:
> W: GPG error: [http://dk.archive.ubuntu.com](http://dk.archive.ubuntu.com) breezy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Then it tells me that apt-get update might fix the problem :???: . Problem is, that's what I'm trying to do.

Any help would be awesome. :)

---

### Post by temcat on 2005-10-16
I have the same problem here.

---

### Post by mohaham on 2005-10-16
did you follow the instructions in this link:
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)

---

### Post by temcat on 2005-10-16
[QUOTE=mohaham]did you follow the instructions in this link:
[https://wiki.ubuntu.com/BreezyUpgradeNotes](https://wiki.ubuntu.com/BreezyUpgradeNotes)[/QUOTE]

I personally didn't, but the for me problem has disappeared by now.

---

### Post by kvidell on 2005-10-16
I don't see anything on there about flushing the PGP finger prints.
How does one do this?
- Kev

---

### Post by moopere on 2005-10-16
[QUOTE=kvidell]I don't see anything on there about flushing the PGP finger prints.
How does one do this?
- Kev[/QUOTE]

Theres something broken at the ubuntu end I think.  Don't mess about too much as you'll end up completly stuffed (I deleted the trusted and keyring files in /etc/apt...arggh!).

Try this instead if you're comfortable with the command line:

[http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599](http://www.ubuntuforums.org/showthread.php?p=416599&posted=1#post416599)

---

### Post by Veracon on 2005-10-17
Magically disappeared for me too.:???:

---

