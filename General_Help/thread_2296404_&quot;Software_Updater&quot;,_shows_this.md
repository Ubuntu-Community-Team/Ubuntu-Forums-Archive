---
title: "&quot;Software Updater&quot;, shows this"
date: 2015-09-25
forum: General Help
---

### Post by happyytilton on 2015-09-25
Don't know if this is the right place for this, but my "Software Updater" responds with this window after manually checking for updates.
Normally I let it automatically check and display the updates, but I'm looking for a Firefox security patch, that's supposed to be coming out.
[ATTACH=CONFIG]264648[/ATTACH]
But my wireless internet connection is good at 54 Mb/s, and the browser and the email client no trouble downloading or uploading.
This has never happened in the past, only here in the last week.

---

### Post by v3.xx on 2015-09-25
Try updating in terminal and check for errors.
```
sudo apt-get update
```

---

### Post by ian-weisser on 2015-09-25
Volunteer-hosted mirrors go down, just like all servers. Mirrors come and go.
Wait a few minutes and try again.
If it recurs, select a different mirror.

---

### Post by grahammechanical on 2015-09-25
Ubuntu has a long list of software sources each with its own URL. If Software Updater fails to make a connection to even one of those URLs we get that error message. It does not stop us updating. I run the development version wily werewolf (15.10) and during the development period some of the repositories are not active. So, I see that message every time I update, which is daily. I just click OK and Updater gets busy updating what it can.

If we see that message on a released version of Ubuntu the culprit often turns out to be a Personal Package Archive (PPA) that we have installed as a repository. PPAs are useful for installing software but many should be disabled afterwards. We do that at System Settings>Software & Updates>Other Software. Running sudo apt-get update as suggested will what particular repositories are unavailable.

Regards.

---

### Post by happyytilton on 2015-09-26
Ok, I see.... Thought something was possibly wrong.
[**[COLOR=#000000]v3.xx[/COLOR]**]("http://ubuntuforums.org/member.php?u=1937239").... Running "sudo apt-get update" showed the problem PPA's and unchecking them in "Software & Updates" removed the "Failure" notices.
Now I see as [**[COLOR=#000000]grahammechanical[/COLOR]**]("http://ubuntuforums.org/member.php?u=1087323") pointed out, it's really no big deal.

Thanks everyone... Marking it SOLVED.

---

