---
title: "Problems using apt install"
date: 2022-09-26
forum: General Help
---

### Post by krockdurr on 2022-09-26
Hi,

I'm using Ubuntu 20.04, and face a problem with .deb packages installation (I hope I'm writing in the good forum).

A recurrent error as below stops every package installation.

```
E: Unable to locate package {name}.deb
```

It may be important to add that every .deb file I tried to install was already downloaded.
I made sure to be in the good folder while in the terminal, to insert the good names of libraries, and to use the good commands.
I  first tried to install the 32 bits libraries of "gamemode" package (on a  64bits computer), and it failed with the error on top. I tried a bunch  of things to help myself out of this problem as:
- Uninstalling entirely the Gamemode package using ```
apt remove gamemode --autoremove
```
- Removing every data in the cache of apt
-  I know too, that with very old apt-get of apt system, I shall put the  deb file in a folder something similar to /var/apt/archives/ and tried,  failed again.

I think I tried 2 to 3 more help guides I found, but  to be honest, I can't remember which and haven't found trace of them in my  internet history.

At this point, I thought "Meh, should be a problem with those gamemode packages" but things seemed too sketchy for me.

Minutes later, I tried to update Discord with the downloaded package, got the exact same error.

I tried for maybe an hour and half, it's kind of driving me crazy.

To  add more precision, I'm not new to Ubuntu, Debian or Linux in general  (I use it actively for personal purposes and development hobby) but I  may use bad vocabulary or need some explanations about process I can't  understand.
(English isn't my mother language, so maybe you'll also see a few mistakes)


Thanks for reading this!

---

### Post by TheFu on 2022-09-26
So ... there's a subtle thing with using 'apt' to install .deb files that isn't 100% intuitive.  The location for the .deb file must have some path part in the specification.

apt-get won't install .deb files no matter how hard anyone tries.
apt will.
dpkg will, but it won't deal with any dependencies, which is why apt is a nicer tool.

Ok, so just to clarify .... 

**This won't work, assuming the .deb file is in the CWD/PWD.**
```
sudo apt install file-version.deb
```
But any of these will work:
```
sudo apt install ./file-version.deb
sudo apt install ../relative/path/to/file-version.deb
sudo apt install /abosolute/path/to/file-version.deb
```

See the subtle difference?
Understanding the difference between absolute and relative paths on every OS ... that includes MS-Windows is a basic skill.
Absolute paths begin with a '/', always.
Relative paths are relative from the PWD - present working directory.  You can look up what pwd/cwd mean and master those quickly.  

Extra credit:
Every running process has a pwd.  That includes programs a human starts, programs started by the system, programs run by cron or systemd or by other users. Understanding the PWD is an important thing, just like knowing which user is running a process.

---

