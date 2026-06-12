---
title: "locale quesiton"
date: 2007-08-28
forum: General Help
---

### Post by satimis on 2007-08-28
Hi folks,


Ubuntu 7.04 lamp server amd64
Vmware 1.0.1
$ uname -r```

2.6.20-15-generic

```


On running;
$ sudo /etc/init.d/httpd.vmware start```

Starting httpd.vmware:
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
        LANGUAGE = (unset),
        LC_ALL = (unset),
        LANG = "en_HK.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").

```
The above warning popup

$ apt-cache policy localeconf```

localeconf:
  Installed: 0.9.4.1
  Candidate: 0.9.4.1
  Version table:
 *** 0.9.4.1 0
        500 http://hk.archive.ubuntu.com feisty/universe Packages
        100 /var/lib/dpkg/status

```
Already installed


Please advise on which file I have to adding following lines;```

setenv LANGUAGE  en_HK.UTF-8
setenv LC_ALL  en_HK.UTF-8

```
~/.bashrc
???

If YES whether add them at the end of the file?

OR is there GUI command to config them?

TIA


B.R.
satimis

---

### Post by raijinsetsu on 2007-08-28
Well, first off, those environment variables in your ~/.bashrc file will not get used by vmware because they're your environment variables, and not the systems.
You should put them in "/etc/profile", "/etc/bashprofile", or one of the similar files(I forget the name, and I'm not in front of a linux box atm).
Hope this helps.

---

