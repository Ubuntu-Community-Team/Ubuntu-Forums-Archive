---
title: "out of curiosity....tmpfs"
date: 2013-06-26
forum: General Help
---

### Post by morswin on 2013-06-26
Hi,

I'm planning to move whole ~/.cache directory (~0.5 GB) to RAM with tpmfs. 

If possible, are there any reasons for not to do this?

Couldn't find answer nowhere.

[COLOR=#000000]Thanks. [/COLOR]:)

---

### Post by dino99 on 2013-06-26
[http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html](http://www.webupd8.org/2013/02/keep-your-browser-profiles-in-tmpfs-ram.html)

---

### Post by Ranko Kohime on 2013-06-26
[LIST]
[*]gnome-disks (formerly palimpsest) will forget any benchmarks that you have performed, as it stores these in ~/.cache/gnome-disks/benchmarks
[*]The ibus daemon keeps what appears to be a configuration file at ~/.cache/ibus
[*]Rhythmbox keeps it's scrobbling data in ~/.cache/rhythmbox
[*]Shotwell keeps it's generated thumbnails in ~/.cache/shotwell, and it does not regenerate them on the fly
[*]Vinagre keeps it's preferences file in ~/.cache/vinagre
[/LIST]

That's just what I found on my system, you may run some applications that I don't that also store their configurations in ~/.cache.

Remember that a tmpfs will delete everything on every reboot.  You may want to take a look and see if anything important is in there prior to taking the plunge.

---

### Post by morswin on 2013-06-26
Thank you!

So, as far as I understand, there are two conclusions:

1. tmpfs works well with dotted files in /home directory.
2. Deleting files on reboot affects only on "third-party apps". OS remains stable. 

That's what I wanted to know and that's great. Personally, I will avoid many gnome-related problems since I do not use any desktop environment.

Best regards,

---

### Post by Ranko Kohime on 2013-06-26
The only other problem you might run into is if you encrypt your home directory, since the home directory is unavailable at mount time.

I tried binding ~/.thumbnails to /tmp (/tmp on my system is on a tmpfs, and I didn't want to create another for ~/.thumbnails), but this failed since my home directory is encrypted, and asked me to wait or skip during boot up.

---

