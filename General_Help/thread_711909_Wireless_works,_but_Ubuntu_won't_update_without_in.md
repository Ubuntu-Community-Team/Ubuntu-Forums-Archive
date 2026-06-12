---
title: "Wireless works, but Ubuntu won't update without internet connection?"
date: 2008-03-01
forum: General Help
---

### Post by Peanutsmypup on 2008-03-01
Well, my girlfriend is done with Windows after the fourth crash in a year.  We have a really old computer that we installed Xubuntu on and she likes it, so we went with Ubuntu since her machine is much more powerful than that old POS.

Anyway, I installed Ubuntu no problems. I configured the Wireless and it worked right off the bat.  However, when i went to add new applications it said:

"The list of applications is not availabe"
"Click on 'Reload' to load it.  To reload the list you need a working internet connection"

So, I hit reload, click on the app I want to add, and the same thing pops up.

Now, I obviously have an internet connection through the wireless network because I'm typing and posting this through the computer in question.  Still, the computer won't recongnize the connection and treat it as the internet connection.

Is there any advice anyone can give?  Has anyone else had this problem and I have simply missed the answer in the forums?  I have scanned everything, and as far as I know I have downloaded, burned, and installed the appropriate version of Ubuntu.  I'm running 7.10 on a Dell Inspiron 6000.

Please help! :)

---

### Post by Peanutsmypup on 2008-03-01
And, no sooner do I post this thread do I find the answer...:KS

[http://ubuntuforums.org/showthread.php?t=683897]("http://ubuntuforums.org/showthread.php?t=683897")

---

### Post by jeffus_il on 2008-03-01
Try this from a terminal:
```
sudo aptitude update
```
and then ```
sudo aptitude upgrade
```

---

### Post by TheWizzard on 2008-03-01
> **Peanutsmypup said:**
> And, no sooner do I post this thread do I find the answer...:KS

[http://ubuntuforums.org/showthread.php?t=683897]("http://ubuntuforums.org/showthread.php?t=683897")

that's why i always have the computer wired to the internet during an ubuntu install.

---

