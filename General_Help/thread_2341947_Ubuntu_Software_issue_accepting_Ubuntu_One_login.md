---
title: "Ubuntu Software issue accepting Ubuntu One login"
date: 2016-11-02
forum: General Help
---

### Post by isolated-thinker on 2016-11-02
Greetings!

I am having issues with the Ubuntu Software program accepting my login credentials when trying to download and install programs labeled as "nonfree." To my knowledge, everyhting is up-to-date.

I am running 16.04 LTS

Here is the screencap.

[IMG]https://uncommongeek.files.wordpress.com/2016/11/screenshot-from-2016-11-02-12-28-17.png[/IMG]

I know I used the correct login info, and even created a new account to test, with the same result.

Anyone else have this issue or know of a fix?

Thank you!

---

### Post by howefield on 2016-11-08
It's a bug : [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943)

If you want to install a snap, try installing from the terminal..

```
sudo snap login xxxxxxxxx@xxxxxx.com
```

Type your password when prompted, you won't see the characters being typed. 
 
Then, when you get the "*Login successful*" message, use the following to install..

```
snap install nameofsnap
```

---

### Post by isolated-thinker on 2016-11-09
> **howefield said:**
> It's a bug : [https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1616943)

If you want to install a snap, try installing from the terminal..

```
sudo snap login xxxxxxxxx@xxxxxx.com
```

Type your password when prompted, you won't see the characters being typed. 
 
Then, when you get the "*Login successful*" message, use the following to install..

```
snap install nameofsnap
```

Thank you! I will give this a shot as soon as I can! 
I am also having the same issue with my newly installed Ubuntu Studio... I'm assuming the same command will work?

---

### Post by howefield on 2016-11-09
> **isolated-thinker said:**
> Thank you! I will give this a shot as soon as I can! 
I am also having the same issue with my newly installed Ubuntu Studio... I'm assuming the same command will work?

Indeed, no matter the flavour assuming that snapd is installed, if you have any issues just post, it'll be an easy enough fix.

One thing I should have said in the post above is that you may get asked for 2 passwords.. first for sudo (depending on how long it was since you last used sudo) and secondly for the SSO login.

---

### Post by isolated-thinker on 2016-11-10
> **isolated-thinker said:**
> Thank you! I will give this a shot as soon as I can! 
I am also having the same issue with my newly installed Ubuntu Studio... I'm assuming the same command will work?

This did the trick!

Thanks a million!

---

### Post by howefield on 2016-11-10
> **isolated-thinker said:**
> Thanks a million!

You're welcome.

---

