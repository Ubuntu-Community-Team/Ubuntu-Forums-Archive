---
title: "How I solved &quot;Error while copying: There was an error getting information about &quot;/&quot;.&quot;"
date: 2015-11-04
forum: General Help
---

### Post by heroquestelf on 2015-11-04
I know that I am probably preaching to the choir on this one, and this is probably a solution that all you 733T 71NUX people already know about, but I recently encountered a bug with my machine and was rather surprised to discover that this is a general bug with Ubuntu and is a problem that a lot of people are having. 

Basically, the glitch shows up when you try and create a desktop shortcut by using Ubuntu's search function. When you go to drag the icon onto the desktop, the computer generates the following error code:

[IMG]http://i.stack.imgur.com/ScyYC.png[/IMG]
There was an error getting information about "/".

One of the original solutions offered was to open up usr/share/applications and drag and drop your icons from there, but this solution was thrown out because it appears that the various applications that are producing this error (in my case, it was Kaffeine) are not putting desktop files into the usr/share/applications folder.

So I decided to create my own .desktop file and put it into the directory so as to create my own icon, but I wasn't certain where the executable was on my machine, so I opened up a terminal and executed a ```
apt-file search Kaffeine
``` and discovered that Kaffeine already had a .desktop file, but it was in the usr/share/app-install folder instead of the usr/share/applications folder. So I opened up THAT folder and created my icon from THAT file instead and it seems to work exactly like it is supposed to. 

Is this an effective solution for all you supercool Ubergeeks out there?

---

### Post by yetimon_64 on 2015-11-04
> **heroquestelf said:**
> ...you 733T 71NUX people...

you "teet tlnux" people ? ... :lol:

Just a quick pointer "leet speak" shouldn't be used here, not only because of the code of conduct/posting guidelines but because that example is hilariously wrong how you've used it. 

1337 = leet, ie "7" is a "t" not an "l" in leet and a "1" is an "l" not an "i" in linux, so you have actually written "teet tlnux" not "leet linux" etc.

Close ... ;)

> ..was rather surprised to discover that this is a general bug with Ubuntu..
Do you have a launchpad link to the "bug" you are pointing out ? 
That is where bugs are listed if they are accepted as a bug etc.

Regards, yetimon_64

---

### Post by QIII on 2015-11-04
If there is no such "bug", you are free to report it.  That's how Canonical gets word of them.

Cheers!

---

### Post by heroquestelf on 2015-11-05
The bug has been reported. That's the reason for this post.

[https://bugs.launchpad.net/unity/+bug/1241972](https://bugs.launchpad.net/unity/+bug/1241972)

---

