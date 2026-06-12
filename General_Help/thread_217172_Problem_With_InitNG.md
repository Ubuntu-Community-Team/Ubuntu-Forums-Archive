---
title: "Problem With InitNG"
date: 2006-07-16
forum: General Help
---

### Post by rowanparker on 2006-07-16
Hello,
I was trying to install InitNG using [this]("https://help.ubuntu.com/community/InitNG") page.

After running the command "Build initng from source package to avoid dependency problems" lower down the page, it failed with a gpg error. Then I followed [this]("http://blog.space-based.de/2006/05/initngs-apt-repo-has-a-new-home/") link and ran the gpg commands but I get the error: ```
rowan@hal:~/.gnupg$ sudo gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 77AFC5B7
gpg: WARNING: unsafe enclosing directory ownership on configuration file `/home/rowan/.gnupg/gpg.conf'
gpg: external program calls are disabled due to unsafe options file permissions
gpg: keyserver communications error: general error
gpg: keyserver receive failed: general error
```

What do I do now?

Thanks, Rowan.

---

### Post by givré on 2006-07-16
You don't need to run that with sudo. Just run it as a normal user. and add the key which is in ~/.gnupg with synaptic.
But the key don't work really good (it will bother you about a main/Source he couldn't found) so, i suggest you to not use the key and to comment the line about initng at the end, to not have the warning.

---

### Post by rowanparker on 2006-07-17
Thank you very much.

I thought I'd tried that but then after a reboot it was fine.


Thanks, Rowan.

---

