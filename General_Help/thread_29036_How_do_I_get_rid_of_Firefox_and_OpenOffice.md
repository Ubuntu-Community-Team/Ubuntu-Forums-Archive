---
title: "How do I get rid of Firefox and OpenOffice?"
date: 2005-04-22
forum: General Help
---

### Post by computerdude33 on 2005-04-22
I'd like to

A. Uninstall OpenOffice.org 1.1.x and replace it with OpenOffice.org 1.979
B. Uninstall Firefox 1.0x and replace it with Firefox 1.03 in a seperate directory (for customization)

How would I go about doing this?

---

### Post by shakin on 2005-04-22
[QUOTE=computerdude33]I'd like to

A. Uninstall OpenOffice.org 1.1.x and replace it with OpenOffice.org 1.979
B. Uninstall Firefox 1.0x and replace it with Firefox 1.03 in a seperate directory (for customization)

How would I go about doing this?[/QUOTE]

You can select to remove them using Synaptic.

I recommend using OpenOffice.org 1.9.95 even though it's not in the repositories. It works way better than 1.9.79. You can grab it at [ftp://openoffice.mirror.cygnal.ca/openoffice/developer/680_m95/OOo_1.9.95_LinuxIntel_install.tar.gz](ftp://openoffice.mirror.cygnal.ca/openoffice/developer/680_m95/OOo_1.9.95_LinuxIntel_install.tar.gz)

All you need to do is extract the tar:
```
$ tar -zxvf OOo_1.9.95_LinuxIntel_install.tar.gz
```

delete the distro-specific rpms (maybe one would work, I didn't try):
```
$ rm *menus*
```

convert the remaining rpms to debs:
```
$ alien *.rpm
```

install the debs:
```
$ dpkg -i *.deb
```

And you're done! No menu will be created, but you can run it from /opt/openoffice.org1.9.95/program/soffice.bin

Edit: I should post this in the how-to forum.

---

### Post by computerdude33 on 2005-04-22
Thanks! (on a side note, I'll stick with the main beta until 2 stable comes out)

---

### Post by Annie Versary on 2005-04-22
[QUOTE=computerdude33]I'd like to

B. Uninstall Firefox 1.0x and replace it with Firefox 1.03 in a seperate directory (for customization)

How would I go about doing this?[/QUOTE]

Is this cause you're facing the same problems as me and others (see [this posting](http://ubuntuforums.org/showthread.php?t=27741&highlight=unable+firefox)) as i.e. described [here](http://os.newsforge.com/os/05/04/19/200205.shtml?tid=152&tid=2) as an unique (K)Ubuntu issue?

Annie

---

### Post by computerdude33 on 2005-04-22
To a degree, I'm doing it because it's easier to install Flash Player in a seperate directory.

---

