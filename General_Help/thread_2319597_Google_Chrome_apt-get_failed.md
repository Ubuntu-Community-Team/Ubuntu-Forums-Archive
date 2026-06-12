---
title: "Google Chrome apt-get failed"
date: 2016-04-05
forum: General Help
---

### Post by kseel on 2016-04-05
Running Ubuntu 14.04 LTS and when I run sudo apt-get update I get the following error: 

W: Failed to fetch [http://dl.google.com/linux/chrome-remote-desktop/deb/dists/stable/Release](http://dl.google.com/linux/chrome-remote-desktop/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)


E: Some index files failed to download. They have been ignored, or old ones used instead.



I have both added [arch=amd64] to my /etc/apt/sources.list.d/google-chrome.list file and added repo_reenable_on_distupgrade="false" to /etc/default/google-chrome file and I am still getting the error.

Any ideas? I am lost.

---

### Post by Bashing-om on 2016-04-05
kseel; Hello;

Must also change the references in the file /opt/google/chrome/cron/google-chrome; lines 24 and 25:
this script also regenerates the .list file .


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by light_yagami2 on 2016-04-05
Are you able to download chrome through the Software Center?

---

### Post by QIII on 2016-04-05
Best way I've figured out how to do it cleanly:

Remove Chrome.

Remove the repo from sources.

Update.

Go to Google's Chrome download site and install fresh.  That will also put the repo without the problem in your sources.

---

### Post by him610 on 2016-04-05
Google no longer supports the 32bit version of Chrome as of 1 March 2016; however, 32bit Chromium is still supported and is available to download from the Ubuntu repository.

---

### Post by QIII on 2016-04-05
Installing chromium does nothing to solve the OP's problem with Chrome.

Let's keep the thread headed in the right direction.

Thanks.

---

### Post by kseel on 2016-04-06
I tried editing /opt/google/chrome/cron/google-chrome and replacing the contents but that still didn't work. I had so many things tied into Google Chrome that I didn't want to uninstall and reinstall like QIII said but that was my only option and worked. 

Thanks!

---

### Post by Habitual on 2016-04-06
> **kseel said:**
> I tried editing /opt/google/chrome/cron/google-chrome and replacing the contents but that still didn't work. I had so many things tied into Google Chrome that I didn't want to uninstall and reinstall like QIII said but that was my only option and worked. 

Thanks!
I've been using
```
deb [arch=amd64] http://dl.google.com/linux/chrome/deb/ stable main
```
since it started barking about "i386 Packages" last week or so.
Not an issue since.

YMMV

---

### Post by deadflowr on 2016-04-06
> **kseel said:**
> <snip> I had so many things tied into Google Chrome that I didn't want to uninstall and reinstall like QIII said but that was my only option and worked. 

Thanks!
Should never be a problem.
Think of it this way: you reinstall Chrome every time you get an update.
Has that ever caused any problems; aside from not being able to update.
(I mean have you ever lost your settings after an update?)

All of YOUR chrome stuff resides in a specially made folder in your own home folder, and uninstalls or updates will never remove that folder.

(It is a perk of Ubuntu's package management system, as it leaves a user's personal folders alone. Allowing uninstalls and reinstalls to flow with ease, and getting the user back into their ways without having to re-configure anything.
The dark side of that is it leaves the user's folder alone, and sometimes it's the user's files and folders that cause the problems and the user needs to manually remove the files themselves.
but those points are irrelevant to this thread)

If you found a solution that works for you, [please mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") to help others

---

