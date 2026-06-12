---
title: "from Ubuntu 11.10 to Precise version"
date: 2013-04-24
forum: General Help
---

### Post by LucDuke on 2013-04-24
Hello, I am Luc
and no Linux techie. Want to upgrade, but in my "Status"there is an error. i know where, but can not change it. permission is set to "Root". The systems tell me I have not enough right to change the Status report. How to solve this??
Everytime as it say's DPKG -running it stops and tell me Missing description..etc..
Have to 1600+ updates waiting.. HELP Wanted,:confused:
Thank you for reading/ helping out.

Luc Van de Steeg -NL.

---

### Post by sandyd on 2013-04-24
Hi, please do not post your email in posts as it usually results in a lot of unwanted emails/spam ending up in your inbox

I have removed your email from the above post.

Thanks!

---

### Post by Impavidus on 2013-04-24
Forget about those 1600+ updates if you want a version upgrade anyway – which is recommendable as 11.10 is almost end of live.

I'm not exactly sure what you mean by your "status". You should be able to open the update-manager. In the upper right it should offer an update to 12.04 LTS. If not, hit "Settings" and select "updates"->report new version: anything but "never". Than hit the upgrade button. Enter your password whenever prompted. Could you tell exactly what's going wrong? If it's difficult to explain, you can always post a screenshot.

It's also possible to do a clean install of 12.04 LTS. Some people prefer clean installs of new versions, but I've never had serious problems upgrading.

---

### Post by LucDuke on 2013-04-24
Hi, thanks for the advise,
tried like you suggested,
still it is not functioning at all
.
package libc-bin is already installedand configured
This keeps coming back- **error install:**
=
package libc6 is already installed andconfigured


pre-dependency problem - not installinglibnih1


package base-files is already installedand configured


package debconf is already installedand configured


package gcc-4.6-base is alreadyinstalled and configured


package libgcc1 is already installedand configured


package libstdc++6 is already installedand configured



installArchives() failed 
=

**And the home/var/lib/dpkg/status error:**
==

Preconfiguring packages ... dpkg: warning: parsing file '/var/lib/dpkg/status' near line 62953 package 'pdfstudio':  missing description==Have no access to the Status-Root has rights, me as the owner/group do have access(limited)

Or this is my digital self-mutulation, or ubu newbie actions, it fucntions all together rather well- Other populair OS would have given up on it-a long time ago..:)
am a user of software, now a little pc-tech, sudo is also new to me, there is nixiepixie and you to ask for help in my necesairy up-grade-new install?-
Thanks everyone for reading&reacting
LucDuke

---

### Post by LucDuke on 2013-04-24
Thank You for the warning.

---

### Post by mörgæs on 2013-04-24
If you are completely new to this I would recommend that you erase the system and do a fresh install. 
13.04 is released very soon. Can you wait a day or two before getting the computer to work?

---

### Post by LucDuke on 2013-04-24
sure, I can wait-thnkz for the tip.

My pc was xp, oemversion. HD broke down, no OS.
Friend's advise to use ubuntu, and i ever since do and update,without problems.
Found this forum by a browser-search.
(what is a Buntu?)

LucDuke

---

### Post by Iowan on 2013-04-24
> **LucDuke said:**
> (what is a Buntu?)


[http://www.ubuntu.com/about/about-ubuntu](http://www.ubuntu.com/about/about-ubuntu)

---

### Post by fantab on 2013-04-24
> **LucDuke said:**
> sure, I can wait-thnkz for the tip.

My pc was xp, oemversion. HD broke down, no OS.
Friend's advise to use ubuntu, and i ever since do and update,without problems.
Found this forum by a browser-search.
(what is a Buntu?)


Ubuntu officially releases other 'FLAVORS' of itself with different [Desktops Environments]("https://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments"), like UNITY (UBUNTU-default/original), KDE (Kubuntu), XFCE (Xubuntu) and LXDE (Lubuntu). This family is sometimes reffered to as "Buntu".

You can download 13.04 from **[HERE]("http://cdimage.ubuntu.com/daily-live/current/")**. Don't worry if it says Beta. Its quite ready and stable for release.

---

