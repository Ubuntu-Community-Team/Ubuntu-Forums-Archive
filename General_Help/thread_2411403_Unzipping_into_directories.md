---
title: "Unzipping into directories"
date: 2019-01-30
forum: General Help
---

### Post by craftsman on 2019-01-30
I am trying to install Android Studio on Ubuntu 18.04.1 and it says to put in /usr/local/ but when I try it says that I do not have authority and I am the only admin. Help me please

---

### Post by HermanAB on 2019-01-30
Unzipping can cause a huge mess if the archive was not created properly.  

The general polite rule is: Always archive a directory, do not archive a bunch of files.

However, some people are not so polite and then when you unarchive something, you can end up with a bazillion files splattered all over the place.

Therefore, if an archive is destined for a system directory, you need to be doubly cautious.  Unarchive it in a subdirectory in your home directory, then if all went well, using sudo, copy it to the system directory.

---

### Post by Impavidus on 2019-01-30
Usually best to package a single directory, but there are cases when putting multiple files or directories at the root of the archive is appropriate. For example, the archive may contains some files meant for /usr/local/share and some others for /usr/local/bin. In that case, creating a share and a bin directory at the root of the archive is appropriate. In other cases, it's just messy. And keep a list of the inventoy of the archive to allow for clean removal later. Also check that you won't overwrite existing files.

Note that unzip has options to list the contents of the archive before unpacking or to unpack into a specific directory. They are explained in the manual:```
# The manual (man can give the manual of most commands). Hit q to exit.
man unzip

# For example, to list the contents before unpacking
unzip -l file.zip

# To unzip into a specific directory instead of the current directory
unzip -d directory file.zip
```

You may be the admin, but the system considers you an ordinary user until you use sudo to act as the root user. This is something you do for all system maintenance. See [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for details.

---

### Post by Holger_Gehrke on 2019-01-30
Just to mention the other option: there is a snap of Android Studio. A simple 'snap install android-studio' in a terminal will install it. According to 'snap info android-studio' it is the current version (3.3.0.20 from 2019-01-14).

Holger

---

