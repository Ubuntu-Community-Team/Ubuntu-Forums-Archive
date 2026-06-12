---
title: "Tor Browser freeze"
date: 2020-03-29
forum: General Help
---

### Post by Tupaq on 2020-03-29
Hello all,
I am using a Zareason Strata on Ubuntu 18.04. I am unable to launch the Tor Browser, even though it is installed and appears in my applications. When I try to launch the Tor Browser, it has frozen my entire laptop while going through the "verifying" stage; the only way I was able to to end this freeze was through closing the lid on my laptop, logging on, and immediately forcing quit for the Tor Browser.
I also noticed that my terminal apparently doesn't recognize the ```
$
``` command in the following code I cut and pasted from [this website]("https://linuxconfig.org/how-to-install-tor-browser-in-ubuntu-18-04-bionic-beaver-linux"):
```
$ sudo apt install torbrowser-launcher
```
This code is when I tried to reinstall the Tor Browser, having forgotten that years ago I had successfully installed and launched it, if only once, before not being able to use it again, and forgetting about it… In any case, I was wondering if anyone else has had this problem, and if they could help me? That would be very much appreciated.

---

### Post by CelticWarrior on 2020-03-30
If you're trying to reinstall then the command should be

```
sudo apt install --reinstall torbrowser-launcher
```

---

### Post by TheFu on 2020-03-30
The '$' prompt is a Unix standard to show you are in a shell, as a non-privileged user.  Basically, not root.
A root prompt would be shown with the '#' prompt.

These nomenclatures are explained very, very, early in any Unix/Linux training and all books.  We all forget that really new people often don't know these basic things.

---

