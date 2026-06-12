---
title: "Software Updater no longer works"
date: 2016-03-10
forum: General Help
---

### Post by ChristmasPi on 2016-03-10
Over the last 10 days, I have noticed that Software Updater no longer works.

The error message that I get is "failed to download repository information, check your internet connection."  I don't believe it is an Internet issue because I get the same error when my device is connected to two different Internet networks and I have no issues accessing any other online resource.

Would someone know how I can fix this issue?

Thank you

---

### Post by v3.xx on 2016-03-10
Open a terminal and enter

```
sudo apt-get update
```

and please post any errors.

---

### Post by QIII on 2016-03-10
Hello!

What release of Ubuntu are you using?  Have you tried changing your repo to main or us (or whatever)?

---

### Post by ChristmasPi on 2016-03-10
@v3.xx - I ran the requested command the message that I get is:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.

@QIII I am running Ubuntu 14.04.  I'm not overly familiar with Ubuntu, so I'm not sure how to change my repo to main or US.

---

### Post by v3.xx on 2016-03-10
Chrome has discontinued the 32bit version.  You need to remove it.

---

### Post by ChristmasPi on 2016-03-10
> **v3.xx said:**
> Chrome has discontinued the 32bit version.  You need to remove it.

I believe that I am using the 64-bit version.

When I go into Chrome=>About, it says [COLOR=#303942][FONT=Ubuntu]Version 48.0.2564.116 (64-bit)[/FONT][/COLOR]

---

### Post by v3.xx on 2016-03-10
Ok, then your source is wrong and I seen a post about this.  Let me go find this post, BB

---

### Post by ChristmasPi on 2016-03-10
> **v3.xx said:**
> Ok, then your source is wrong and I seen a post about this.  Let me go find this post, BB

Thank you, I appreciate this.  I'm not sure how my source is wrong or why it was changed because I've never manually made any changes.

It's getting a bit late in my neck of the woods, but I will try your suggestion(s) in the morning.  Thank you again for your help.

---

### Post by deadflowr on 2016-03-10
Source is fine.
The sources are borked because of google.
Simple fix:
```
sudo sed -i -e 's/deb http/deb [arch=amd64] http/' "/etc/apt/sources.list.d/google-chrome.list"
```
this will add the section [arch=amd64] to the repostiory listing.
it's a temporary fix, but will allow updates to run smooth.

See here for more:
[http://ubuntuforums.org/showthread.php?t=2315941](http://ubuntuforums.org/showthread.php?t=2315941)

---

### Post by v3.xx on 2016-03-10
Well I'm not finding it.  Maybe Qlll knows.  Anyhow the link you have posted above links to an empty download file.  It needs to be replaced with the proper link.  I use  the chromium browser and not sure about chrome.  Maybe Qlll knows.  I'll continue to look :)

Edit:  You the man deadflowr :)

---

### Post by QIII on 2016-03-10
Actually, whaI finally did was to uninstall Chrome, remove the repo from my sources completely, update and then go to the Google Chrome download/install site and let the installer add the sources list entry and install the package.

---

### Post by ChristmasPi on 2016-03-14
> **QIII said:**
> Actually, whaI finally did was to uninstall Chrome, remove the repo from my sources completely, update and then go to the Google Chrome download/install site and let the installer add the sources list entry and install the package.

How do you go about uninstalling Chrome?  

I went into the Ubuntu Software Center and I don't see Chrome listed.  The only thing I see is Chromium.  

Thank you

---

