---
title: "Unable to update Google Chrome"
date: 2013-10-15
forum: General Help
---

### Post by WeAreLinux on 2013-10-15
According to Google's Chrome Releases Blog @ [http://googlechromereleases.blogspot.com/](http://googlechromereleases.blogspot.com/) , a new version of Google Chrome is available today but for some reason I'm unable to update via Update Manager. Update Manager does list the update, but its unchecked and I'm unable to check it :-/ 

Update Manager displays.....

The web browser from Google
google-chrome-stable (Size: 42.3MB)

Changes for the versions:
Installed version: 30.0.1599.66-1
Available version: 30.0.1599.101-1

This update does not come from a source that supports changelogs.

Software Sources have the Google repo enabled/checked ([http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main) and Google's Auth Key is listed. 

When trying to update via command with sudo apt-get upgrade then sudo apt-get upgrade, it displays that google-chorme-stable package will be kept back. 

Suggestions? 

Thanks

---

### Post by Bashing-om on 2013-10-15
WeAreLinux; Hi !

Not a problem to update Chrome for me.
> 
Setting up google-chrome-stable (30.0.1599.101-1) ...

Must be something within you system. 
Post back the output of the terminal codes:
```

sudo apt-get update
sudo apt-get upgrade

```
The place to start troubleshooting.


[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by vasa1 on 2013-10-15
Are you on 32-bit? If so, you may have run into a bug: [http://askubuntu.com/questions/359530/google-chrome-update-wont-install-due-to-unmet-dependencies/359664#359664](http://askubuntu.com/questions/359530/google-chrome-update-wont-install-due-to-unmet-dependencies/359664#359664)

---

### Post by PaulW2U on 2013-10-16
> **vasa1 said:**
> Are you on 32-bit? If so, you may have run into a bug: [http://askubuntu.com/questions/359530/google-chrome-update-wont-install-due-to-unmet-dependencies/359664#359664](http://askubuntu.com/questions/359530/google-chrome-update-wont-install-due-to-unmet-dependencies/359664#359664)

Thanks vasa1, that confirms what I've found here. It's a problem only on 32-bit systems.

---

### Post by tigerjack89 on 2013-10-17
> **PaulW2U said:**
> Thanks vasa1, that confirms what I've found here. It's a problem only on 32-bit systems.
Not too sure tbh, I'm on a 64 bit and have the same problem
```

Changes for google-chrome-stable:i386 versions:
Installed version: 30.0.1599.66-1
Available version: 30.0.1599.101-1


This update does not come from a source that supports changelogs.

```

```

sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  google-chrome-stable:i386
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

---

### Post by vasa1 on 2013-10-17
But you show "google-chrome-stable:i386" which is 32-bit. Isn't there a 64-bit version for you?

---

### Post by Papi47 on 2013-10-17
This may help us.  When I try to upgrade I get

google-chrome-stable:
 Depends: lib32gcc1 (>=1:4.1.1) but it is not installable
 Depends: lib32stdc++6 (>=4.6) but it is not installable
 Depends: libc6-i386 (>=2.11) but it is not installable

---

### Post by PaulW2U on 2013-10-17
For the more adventurous the fix or work around can be found at:

[https://code.google.com/p/chromium/issues/detail?id=304017#c27](https://code.google.com/p/chromium/issues/detail?id=304017#c27)

It worked here, in fact I'm using the new version to post this. Use at you own risk. If it messes up your system, don't blame me. :)

Hopefully, a proper fix will be released soon.

Thanks to [this]("http://www.kubuntuforums.net/showthread.php?63842-google-chrome-stable-can-t-be-installed&p=337114&viewfull=1#post337114") post for pointing me in the right direction.

---

### Post by WeAreLinux on 2013-10-29
Sorry for the late reply. I dont use my computer very often these days. The last time I used my computer was my original post,lol.

>  vasa1

    Re: Unable to update Google Chrome
    Are you on 32-bit? If so, you may have run into a bug: [http://askubuntu.com/questions/35953.../359664#359664](http://askubuntu.com/questions/35953.../359664#359664) 

Thnx for the link. I am using 32-bit...so guess that was the problem. Was able to update Chrome today without problem:

```


Get:1 http://dl.google.com/linux/chrome/deb/ stable/main google-chrome-stable i386 30.0.1599.114-1 [42.2 MB]

Preparing to replace google-chrome-stable 30.0.1599.66-1 (using .../google-chrome-stable_30.0.1599.114-1_i386.deb) ...

Unpacking replacement google-chrome-stable ...

Setting up google-chrome-stable (30.0.1599.114-1) ...


```

Solved! Thnx again.

---

