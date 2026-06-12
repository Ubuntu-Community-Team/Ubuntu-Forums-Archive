---
title: "update problem"
date: 2008-07-03
forum: General Help
---

### Post by sn0m on 2008-07-03
Fellas
I recieved a few updates but when they try to install themeselves, i get an error message.
this is the output

E: /var/cache/apt/archives/openoffice.org-l10n-en-gb_1%3a2.4.1-1ubuntu2_all.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/ttf-opensymbol_1%3a2.4.1-1ubuntu2_all.deb: short read in buffer_copy (backend dpkg-deb during `./usr/share/doc/ttf-opensymbol/changelog.gz')
E: /var/cache/apt/archives/linux-restricted-modules-2.6.24-19-generic_2.6.24.13-19.44_i386.deb: corrupted filesystem tarfile - corrupted package archive
E: /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.13-19.44_i386.deb: corrupted filesystem tarfile - corrupted package archive

Any help
cheers
Sokol

---

### Post by iaculallad on 2008-07-03
Try doing the terminal commands below one-at-a-time:

```
sudo rm /var/cache/apt/archives/firefox_2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb

sudo rm /var/cache/apt/archives/openoffice.org-l10n-en-gb_1%3a2.4.1-1ubuntu2_all.deb

sudo rm /var/cache/apt/archives/ttf-opensymbol_1%3a2.4.1-1ubuntu2_all.deb 

sudo rm /var/cache/apt/archives/linux-restricted-modules-2.6.24-19-generic_2.6.24.13-19.44_i386.deb

sudo rm /var/cache/apt/archives/xorg-driver-fglrx_1%3a7.1.0-8-3+2.6.24.13-19.44_i386.deb
```

Then:

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by sn0m on 2008-07-03
Hi thanks for your reply. This is what I get

sn0m@sn0m-laptop:~$ sudo rm /var/cache/apt/archives/firefox_2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb
rm: cannot remove `/var/cache/apt/archives/firefox_2.0.0.2+0dfsg-0ubuntu0.6.10_i386.deb': No such file or directory
sn0m@sn0m-laptop:~$ 

regards
Sokol

---

### Post by sn0m on 2008-07-04
Hi it was so easy, just a matter of familiarising myself with linux different directories.
Just rm the corrupted downloads and reupdated, everything's fine now.
thanks for your help guys
ta
Sokol

---

