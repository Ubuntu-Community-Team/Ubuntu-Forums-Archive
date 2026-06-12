---
title: "Font rendering"
date: 2008-01-06
forum: General Help
---

### Post by mrk112 on 2008-01-06
I've just got a new laptop and installed Ubuntu 7.10..

The fonts didn't look quite right and after searching the forums I found a couple of commands / utilities that made my fonts look a lot better. They are:

```
sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig
```

But does anyone know what files are altered by doing this? I have another distribution on my desktop computer and it doesn't have the above commands / utilities available (it's not a Debian based distro)..

Thanks..

---

### Post by nick_h on 2008-01-06
Quite a few files under the /etc/fonts directory.

Type:
```
dpkg -L fontconfig-config
dpkg -L fontconfig
```
to see the files. (or use Synaptic package manager)

---

### Post by mrk112 on 2008-01-06
Surely the dpkg-reconfigure command doesn't alter all the files that the fontconfig-config package contains? I thought it would just change a config file?

---

### Post by nick_h on 2008-01-06
Correct - it will just change one or more of the files under the /etc/fonts directory.  It is this directory that contains the system-wide configuration files for fonts.

If you want to know what files were actually modified, run the re-configuartion again and then immediately run:
```
find /etc/fonts -mmin -1 -print
```

---

### Post by mrk112 on 2008-01-06
Thanks..

I'm testing this on a live cd so it was the default settings when it booted up.. I then changed the settings to what I prefer and then back to the defaults to see how the files had been altered.. Here's what I did:

```
ubuntu@ubuntu:~$ sudo dpkg-reconfigure fontconfig-config
ubuntu@ubuntu:~$ find /etc/fonts -mmin -1 -print
/etc/fonts
/etc/fonts/conf.d
/etc/fonts/conf.d/70-no-bitmaps.conf
/etc/fonts/conf.d/10-autohint.conf
/etc/fonts/conf.d/30-defoma.conf
ubuntu@ubuntu:~$ cp /etc/fonts/conf.d/70-no-bitmaps.conf .
ubuntu@ubuntu:~$ cp /etc/fonts/conf.d/10-autohint.conf .
ubuntu@ubuntu:~$ cp /etc/fonts/conf.d/30-defoma.conf .
ubuntu@ubuntu:~$ sudo dpkg-reconfigure fontconfig-config
ubuntu@ubuntu:~$ diff 70-no-bitmaps.conf /etc/fonts/conf.d/70-no-bitmaps.conf 
ubuntu@ubuntu:~$ diff 10-autohint.conf /etc/fonts/conf.d/10-autohint.conf 
diff: /etc/fonts/conf.d/10-autohint.conf: No such file or directory
ubuntu@ubuntu:~$ diff 30-defoma.conf /etc/fonts/conf.d/30-defoma.conf
```

As far as I can tell, the only difference is that with the default settings, the 10-autohint.conf file is not present and with my preferred settings it is. Am I correct?

EDIT: How can I search inside the config files to see if anything refers to /etc/fonts/conf.d/10-autohint.conf?

---

### Post by nick_h on 2008-01-06
Read the file /etc/fonts/conf.avail/README - it looks like all the configuration does is make appropriate symlinks in the conf.d directory.  Then the files in the conf.d directory are read by the fontconfig package.

It looks like all you will need to do is make a symlink.

Have you checked to see if dpkg-reconfigure fontconfig changes anything as well as dpkg-reconfigure fontconfig-config ?

---

### Post by mrk112 on 2008-01-06
Well I see the same change if I skip the second command and just log out and back in again..

I made the symlink in my other distribution but it had no effect.. It must be something else in the way the Ubuntu packages are done.

---

### Post by nick_h on 2008-01-06
At this point my knowledge of this runs out.  There is a manual page.
```
man fonts-conf
```

---

