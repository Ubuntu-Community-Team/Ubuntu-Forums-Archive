---
title: "[SOLVED] Finding reason for updates before installing"
date: 2008-05-30
forum: General Help
---

### Post by unutbu on 2008-05-30
You know how update-manager (the orange box with a star on your gnome panel) gives you a synopsis of Changes and a Description for each package update?

Is there a way I can find out this information without update-manager and without installing the package?

A CLI command would be great, but even a website would be okay.

I tried poking around at [http://packages.ubuntu.com/](http://packages.ubuntu.com/) but it appears that website does not provide any information on security updates.

---

### Post by forestpixie on 2008-05-30
Does this help at all

[http://www.ubuntu.com/usn](http://www.ubuntu.com/usn)

---

### Post by unutbu on 2008-05-30
Thanks forestpixie, that site is very useful. 
Using wireshark I discovered that update-manager gets its changelogs from [http://changelogs.ubuntu.com](http://changelogs.ubuntu.com).

Using commands like
```
% apt-cache show openoffice.org-writer | grep Filename
Filename: pool/main/o/openoffice.org/openoffice.org-writer_2.3.0-1ubuntu5.4_i386.deb

```

it is possible to guess the url of the changelog:
[http://changelogs.ubuntu.com/changelogs/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/o/openoffice.org/openoffice.org_2.3.0-1ubuntu5.4/changelog)

The algorithm to go from apt-cache output to the changelog url is still a bit fuzzy to me (because the url for some packages seem to follow a different pattern), but at least I know now where update-manager is getting its  information.

And after all that work, I think the site you cited is more informative.

Thanks very much for your help!

---

### Post by forestpixie on 2008-05-31
THis also might be of interest

[http://patches.ubuntu.com/](http://patches.ubuntu.com/)

---

