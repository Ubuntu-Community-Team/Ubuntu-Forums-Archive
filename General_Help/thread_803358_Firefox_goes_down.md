---
title: "Firefox goes down"
date: 2008-05-22
forum: General Help
---

### Post by Kane_of_NOD on 2008-05-22
Hello

I just installed Ubuntu 8.04, and I am trying to migrate to Linux world, but every day comes a new problem and then I go back to windows...

Todays problem: 

I was watching some youtube videos, and then, firefoc 3 Beta 5 goes down. Like when I close it, Just Like that, i did nothing (no Alt+F4 or something)...

Whats wrong?

I started Firefox again.. and i went to youtube and them.. Puff, fire on screen, firefox went down!

I am using compiz with some plugins like Atlantis and stuff.
All my other programs are excelent, i play FPS games online, my internet connection is ADSL2+...

Whats worng?

=(

---

### Post by adityakavoor on 2008-05-22
Do an update once. the xulrunner update is required for firefox to run properly.

```
sudo update-manager -d
```

---

### Post by Kane_of_NOD on 2008-05-22
Yes .. My system is up to date.  =)

$ sudo apt-get update
$ sudo apt-get upgrade

:)

its all good.. the problem  is firefox.. !!

---

### Post by sizzam on 2008-05-27
I was having the same problem with Flash videos crashing Firefox.  There is an open bug ticket for this here:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888)


I corrected the problem for myself with steps gleaned from the bug ticket, details are in this post:

[http://ubuntuforums.org/showpost.php?p=5057137&postcount=5](http://ubuntuforums.org/showpost.php?p=5057137&postcount=5)

I have been crash-free since performing these steps.

---

### Post by Kane_of_NOD on 2008-05-28
Didn't work  =(

I downgraded to Firefox 2.0

and it continues to go down... 

I think that it could be a conflict with Compiz.. 
But, what plugin?? what visual effect is causing this?


I need some help, please!!

---

### Post by ubuntu-freak on 2008-05-28
It's the libflashsupport package. Run this command:
 
**sudo apt-get purge flashplugin-nonfree libflashsupport**

Now skip to the manual install method for Flash in Part 1 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683), then download and install v10 beta.
 
Nathan

---

### Post by michelux on 2008-05-28
I had the same problem with FF3B5.
The way I solved this problem was by upgrading Firefox to RC1, and now all is working fine again.

I used this instruction to upgrade:
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)

---

### Post by Kane_of_NOD on 2008-05-28
I did that yesterday....


The problem presists

---

### Post by Kane_of_NOD on 2008-05-28
> **michelux said:**
> I had the same problem with FF3B5.
The way I solved this problem was by upgrading Firefox to RC1, and now all is working fine again.

I used this instruction to upgrade:
[http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html](http://www.ubuntugeek.com/how-to-install-firefox-3-rc1-in-ubuntu-hardy.html)



and my language?

i am portuguese. Does firefox remains in portuguese?

:confused:

---

### Post by ubuntu-freak on 2008-05-28
> **Kane_of_NOD said:**
> I did that yesterday....


The problem presists

 
Did you try my suggestion?
 
Nathan

---

### Post by Kane_of_NOD on 2008-05-28
> **reassuringlyoffensive said:**
> Did you try my suggestion?
 
Nathan



yes Nathan, i did...

All the tutorial actually. :S


:(:(

---

### Post by michelux on 2008-05-28
> **Kane_of_NOD said:**
> and my language?

i am portuguese. Does firefox remains in portuguese?

:confused:

From what I read on the webpage I posted you might lose your language pack..

quote:
'After installing Firefox 3 Release Candidate 1, the language packages (xulrunner) are not recognized. Any help would be appreciated.

Don’t install this upgrade if you want to keep your language packs.'


I have installed the English version of FF so I can't tell you what the effect of this update is on your language pack

---

### Post by Kane_of_NOD on 2008-05-28
Remains the same  :S


I did what you said, Nathan, again..

And it just goes down... :S


I still think that it is some kind of plugin or stuff that I activated in Compiz manager that is conflicting with Firefox and Flashplayer stuff

:)   What do you think?  (I'm just a noob)  :(    ~yet~ LOL

---

### Post by ubuntu-freak on 2008-05-28
> **Kane_of_NOD said:**
> Remains the same  :S


I did what you said, Nathan, again..

And it just goes down... :S


I still think that it is some kind of plugin or stuff that I activated in Compiz manager that is conflicting with Firefox and Flashplayer stuff

:)   What do you think?  (I'm just a noob)  :(    ~yet~ LOL

 
Have you disabled any add-ons you have in Firefox? Test performance with effects disabled also.
 
Nathan

---

