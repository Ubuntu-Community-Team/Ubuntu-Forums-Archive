---
title: "Chrome - Failed to fetch"
date: 2016-03-07
forum: General Help
---

### Post by zkab on 2016-03-07
I get this when updating Ubuntu:

W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)
E: Some index files failed to download. They have been ignored, or old ones used instead.

OK - I googled and found that the reason is that support is dropped for 32-bits Chrome:
"Since Google dropped support for 32-bit Chrome on Linux an error occurs when updating apt in 64-bit systems (with multi arch enabled)"

The solution is to insert "[arch=amd64]" in "/etc/apt/sources.list.d/google-chrome.list" so it looks like this:
deb [arch=amd64] [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main

After that I didn't get errors when updating - but problem is that this file is automatically configured so any modifications made will disappear after awhile ... and that is true.
How do I make this change permanent so I don't have  to insert "[arch=amd64]" in "/etc/apt/sources.list.d/google-chrome.list"  every time I make an uppdate ?

---

### Post by egeezer on 2016-03-07
A way to do what you want was given on Distrowatch   [http://distrowatch.com/weekly.php?issue=20160307](http://distrowatch.com/weekly.php?issue=20160307)  in the Miscellaneous News section.

---

### Post by Bashing-om on 2016-03-07
zkab; Hello ..

Uh Huh .. Why the edited file gets re-written can drive you nuts, or make you very comfortable with this our operating system by choice. Both ? 

Anyway, /etc/apt/sources.list.d/google-chrome.list gets generated from within the script /opt/google/chrome/cron/google-chrome .

In this file also add the " [arch=amd64] " edit . In my install this was lines 24 and 25 .

[INDENT][INDENT]inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by zkab on 2016-03-08
Thanks for the solution ... Agoegeezer & Bashing-om

---

### Post by slickymaster on 2016-03-08
*Moved to the ***General Help*** sub-forum*

@zkab:
Please don't forget to mark your thread as [solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")

---

### Post by theroadconnection on 2016-03-08
The DistroWatch fix didn't work for me. I did come across a fix on an Ubuntu Group on Linked in and this worked for me on Mint: [https://feliciano.tech/blog/google-chrome-causing-apt-get-update-fail-heres-fix/](https://feliciano.tech/blog/google-chrome-causing-apt-get-update-fail-heres-fix/)

---

