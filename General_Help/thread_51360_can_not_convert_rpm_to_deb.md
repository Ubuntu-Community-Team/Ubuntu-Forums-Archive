---
title: "can not convert rpm to deb"
date: 2005-07-23
forum: General Help
---

### Post by nickname on 2005-07-23
Hi I'm new to Ubuntu

I'm using Hoary Hedghog, and I've updated all my repositories and have alien installed. However whenever I try to convert an RPM into deb file so I can install it I get these errors

mkdir: cannot create directory `RealPlayer10GOLD.rpm:': Invalid argument
mkdir: cannot create directory `read': File exists
mkdir: cannot create directory `manifest': File exists
mkdir: cannot create directory `failed:': Invalid argument
mkdir: cannot create directory `Success': File exists
sh: line 1: -RealPlayer10GOLD.rpm:: command not found
chmod: cannot access `RealPlayer10GOLD.rpm:': No such file or directory
chmod: cannot access `failed:': No such file or directory
sh: line 1: -RealPlayer10GOLD.rpm:: command not found
sh: -c: line 2: syntax error near unexpected token `;'
sh: -c: line 2: `; cpio --extract --make-directories --no-absolute-filenames --preserve-modification-time) 2>&1'
Unsuccessful stat on filename containing newline at /usr/share/perl5/Alien/Package/Rpm.pm line 166.
mkdir: cannot create directory `RealPlayer10GOLD.rpm: read manifest failed: Success\n-RealPlayer10GOLD.rpm: read manifest failed: Success\n/RealPlayer10GOLD.rpm: read manifest failed: Success\n': No such file or directory
mv: invalid option -- R
Try `mv --help' for more information.
find: RealPlayer10GOLD.rpm:: No such file or directory
find: failed:: No such file or directory
sh: line 1: -RealPlayer10GOLD.rpm:: command not found
sh: line 2: -type: command not found
Argument "RealPlayer10GOLD.rpm:" isn't numeric in bitwise and (&) at /usr/share/perl5/Alien/Package/Rpm.pm line 216, <GETPERMS> line 1.
Unsuccessful stat on filename containing newline at /usr/share/perl5/Alien/Package/Rpm.pm line 235, <GETPERMS> line 1.
mkdir: cannot create directory `RealPlayer10GOLD.rpm:': Invalid argument
mkdir: cannot create directory `read': File exists
mkdir: cannot create directory `manifest': File exists
mkdir: cannot create directory `failed:': Invalid argument
mkdir: cannot create directory `Success': File exists
sh: line 1: -RealPlayer10GOLD.rpm:: command not found
sh: line 2: /debian: No such file or directory
sh: -c: line 2: syntax error near unexpected token `;'
sh: -c: line 2: `; patch -p1)'
find: RealPlayer10GOLD.rpm:: No such file or directory
find: failed:: No such file or directory
sh: line 1: -RealPlayer10GOLD.rpm:: command not found
sh: line 2: -name: command not found
patch failed with .rej files; giving up at /usr/share/perl5/Alien/Package/Deb.pm line 306, <GETPERMS> line 1.
find: RealPlayer10GOLD.rpm: read manifest failed: Success
-RealPlayer10GOLD.rpm: read manifest failed: Success
: No such file or directory


can somebody please help!!!

---

### Post by Xian on 2005-07-23
Not all rpm's can be converted. To install Realplayer you should either use the bin installer available from their webpage, or just follow the starter guide [instructions](http://ubuntuguide.org/#realplayer).

---

### Post by nickname on 2005-07-24
Well I've tried using following the steps in the guide and using Synaptic Package manager. Real player appears to install fine, but when I launch it, it doesn't load properly. WHen I do a ps -ax I can see the daemon, but the real player window doesn't load up, it's like the daemon's frozen.

---

