---
title: "Programs missing from Software Center?"
date: 2015-10-12
forum: General Help
---

### Post by MachFront on 2015-10-12
Only yesterday I set up a dual-boot. I ran a factory reset of my Win 7, cleaned out bloatware and reduced the partition. I then installed Lubuntu on the remainder.

I had installed Lubuntu before on my gal's laptop and it never recognized anything plugged into her usb ports. I replaced it with Mint but the issue persists.
Point is, I spent a lot of time messing about with Lubuntu and I never came across this.

When I run the Lubuntu Software Center, first of all, when I type in the search it pauses after a letter or two, then takes about 10-20 secs before it finishes what I typed.

I ran a search for VLC to install it...and it's not there.
Likewise Clementine.

I know these programs were in the software center because I installed them on my girlfriend's machine.
What's going on?

And what's with my cursor appearing in random spots while I'm typing? It's done it four times while writing this.

---

### Post by vasa1 on 2015-10-12
Try *apt-cache policy clementine* and *apt-cache policy vlc* and post the output here.

Have you enabled "universe"?

Also, please ask just one question with an appropriately descriptive title per thread. It makes it easier for others to follow.

---

### Post by grahammechanical on 2015-10-12
Yesterday I searched for an application in software centre and  got a result but when I clicked to get more information I was informed that the application was not in the software centre. This happens when we do not have the muiltverse or partner repositories enabled.

---

### Post by vasa1 on 2015-10-12
And you can read more about repositories here: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by MachFront on 2015-10-13
> **vasa1 said:**
> Try *apt-cache policy clementine* and *apt-cache policy vlc* and post the output here.

Have you enabled "universe"?


clementine:
  Installed: (none)
  Candidate: 1.2.0+dfsg-2build1
  Version table:
     1.2.0+dfsg-2build1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
eric@eric-HP-2000-Notebook-PC:~$

vlc:
  Installed: (none)
  Candidate: 2.1.6-0ubuntu14.04.1
  Version table:
     2.1.6-0ubuntu14.04.1 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/universe amd64 Packages
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe amd64 Packages
     2.1.2-2build2 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
eric@eric-HP-2000-Notebook-PC:~$


And yes, 'universe' is enabled. It is by default I assume since I didn't change anything regarding respositories.
But, I just loaded Software Center again and still these programs won't appear. Plug-ins relevant to them do, however. ???

---

### Post by MachFront on 2015-10-13
Poking about I see the same is true to GIMP and Chromium. Plug-ins, data, extentions, language files, etc. are present but the programs themselves are not present (in Software Center).

---

### Post by MachFront on 2015-10-15
I attempted to launch Lubuntu Software Center from terminal and had left terminal open when the Center was launched.
When I clicked the Audio and Video button this appeared in the terminal:

DEBUG 2015-10-15 21:43:56,439 run 92 sensitive!


Then I began to enter text in the search field and this appeared in terminal:

/usr/lib/python2.7/dist-packages/LSC/widgets/searchentry.py:58: Warning: Source ID 185 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)
/usr/lib/python2.7/dist-packages/LSC/widgets/searchentry.py:58: Warning: Source ID 205 was not found when attempting to remove it
  GLib.source_remove(self.timeout_id)

Hrm?

So I read way too much online and attempted the purge and reinstall command and it told me that it was unable to do so because it "can not be downloaded".

Hrrmm?

Ssooo....it would seem the Software Center is broken somewhere, but I'm too ignorant to understand the how or why or what solution to apply.

---

