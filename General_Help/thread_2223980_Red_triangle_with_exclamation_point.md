---
title: "Red triangle with exclamation point"
date: 2014-05-13
forum: General Help
---

### Post by ddubbz1979 on 2014-05-13
So what's up with the red triangle in my notification bar and the failing 404 file not found when I update?

---

### Post by lisati on 2014-05-13
Which version of Ubuntu are you using?

---

### Post by squakie on 2014-05-13
It means 1 or more of the repositories isn't responding - perhaps it just doesn't exist, or perhaps it is having problems.  If you have added PPA's so you could down load 3rd party software you can run into this - particularly if you update to a new release.  Right now I leave mine alone as I know my problem is with Handbrake.

I would suggest hovering your mouse over the symbol - it nothing show then click on it.  It will display a message for you.  I'm currently on the Windows side of my dual-boot or I would tell you exactly how to display the message.

If you open a terminal and type:

sudo apt-get update <press enter>

it will try to reload the package list from all the repositories.  You'll be able to see there which repository is failing.

---

### Post by ddubbz1979 on 2014-05-14
I'm running raring ringtail.  Just appeared couple of days ago.  It tells me to update manually and watch for failing repositories.  But when I hit show updates, it says its up to date.

---

### Post by squakie on 2014-05-14
Just do the sudo apt-get update in a terminal window.  It may get all done and say it's up to date, but the failed repository will show if you watch the screen.

---

### Post by Elfy on 2014-05-14
> **ddubbz1979 said:**
> I'm running **_raring ringtail_**.  Just appeared couple of days ago.  It tells me to update manually and watch for failing repositories.  But when I hit show updates, it says its up to date.

13.04 has been EOL since January.

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Keep up to date on version EOL dates or use an LTS ;)

---

