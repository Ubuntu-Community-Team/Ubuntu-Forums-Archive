---
title: "Synaptic and Ubuntu Software Center crash"
date: 2013-01-18
forum: General Help
---

### Post by userfriendly1992 on 2013-01-18
Synaptic and Ubuntu Software Center keeps crashing. I get these following messages:

[IMG]http://s1132.beta.photobucket.com/user/billy_m400/media/Screenshotfrom2013-01-18003022_zps33cce38c.png.html?sort=3&o=0[/IMG]
[ATTACH]230234[/ATTACH]

[ATTACH]230235[/ATTACH]

[IMG]http://s1132.beta.photobucket.com/user/billy_m400/media/Screenshotfrom2013-01-18002848_zps27c18645.png.html?sort=3&o=1[/IMG]

If pictures for some reason do not show, PM me for my email.

---

### Post by userfriendly1992 on 2013-01-18
And for what it's worth, I am running Ubuntu 12.04

---

### Post by Elfy on 2013-01-18
It appears that you have source list issues - it would have been easier to move the System error box :)

No matter - please make sure software centre or synaptic are closed, open a terminal with Ctrl Alt T then run

```
sudo apt-get update
```

It will ask for password - when you type it - it will not appear, this is normal.

Once apt-get has run please copy and paste the WHOLE output to a new post

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by userfriendly1992 on 2013-01-18
```
E: Malformed line 6 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```

Did do that correctly?  I sincerely apologize, I am somewhat new. (I have ran Linux on several computers) However I have never had these kinds of issues..

---

### Post by Elfy on 2013-01-18
Yep that's fine :)

Lines in sources.list should on ever be deb deb-source or # you've got something wrong at line 6

Run ```
cat /etc/apt/sources.list
``` from term and paste it _all_ here please :)

---

### Post by userfriendly1992 on 2013-01-18
```
# /etc/apt/sources.list

deb http://archive.ubuntu.com/ubuntu/ precise main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ precise-security main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ precise-updates main restricted universe multiverse
deb http://archive.canonical.com/ partner
deb-src http://archive.canonical.com/ partner

```

---

### Post by Paqman on 2013-01-18
Go into Software Sources and uncheck the partner repository, then try your update again. If that works, try re-enabling the partner repo and do another update.

---

### Post by userfriendly1992 on 2013-01-18
> **Paqman said:**
> Go into Software Sources and uncheck the partner repository, then try your update again. If that works, try re-enabling the partner repo and do another update.

How do I go about doing that?

---

### Post by userfriendly1992 on 2013-01-18
```
E: Malformed line 6 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
```

This what I got after running: sudo apt-get update

---

### Post by userfriendly1992 on 2013-01-18
I also ran Update Manager and ran into the same errors as Synaptic and Ubuntu Software Center.

---

### Post by Paqman on 2013-01-18
> **userfriendly1992 said:**
> How do I go about doing that?

[LIST=1]
[*]Hit the Windows key and start typing "Software" until Software Sources pops up, click on it.
[*]Go to the Other Software tab (IIRC)
[*]Uncheck "Canonical Partners" and the source code of the same
[*]Try running an update through Synaptic or Software Centre
[/LIST]

---

### Post by userfriendly1992 on 2013-01-18
Complete success!

I did some digging and found this thread from another ubuntu forum:

[http://askubuntu.com/questions/78951/how-do-i-remove-a-malformed-line-from-my-sources-list](http://askubuntu.com/questions/78951/how-do-i-remove-a-malformed-line-from-my-sources-list)

If anyone sees someone with an error similar to mine show them this.
Now could I kindly ask someone to close this thread? Or how do I show that it is solved?

---

### Post by Paqman on 2013-01-18
Top right > thread tools.

---

### Post by userfriendly1992 on 2013-01-18
> **Paqman said:**
> Top right > thread tools.

All it shows is "show printable version."

---

