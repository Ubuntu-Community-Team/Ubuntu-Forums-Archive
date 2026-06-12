---
title: "Dropbox not showing in system tray"
date: 2014-12-28
forum: General Help
---

### Post by sorokin-nbt on 2014-12-28
I recently did a clean upgrade to Xubuntu 14.04 (from 13) and for some reason Dropbox isn't showing in the system tray anymore.
Of course, I've already googled for some solution but none of them worked. Is there any definite solution that worked for anyone out there (specifically for Xubuntu)?

Edit: It partly works when I restarts it (dropbox stop && dropbox start), only sometimes though.

---

### Post by bashiergui on 2014-12-29
Looks like Dropbox doesn't support Xubuntu. 

Have you tried this? I can't vouch for it as I don't use xubuntu. [http://mangel312.blogspot.com/2014/06/setting-up-dropbox-in-xubuntu.html](http://mangel312.blogspot.com/2014/06/setting-up-dropbox-in-xubuntu.html)

---

### Post by vasa1 on 2014-12-29
> **bashiergui said:**
> Looks like Dropbox doesn't support Xubuntu. 

Have you tried this? I can't vouch for it as I don't use xubuntu. [http://mangel312.blogspot.com/2014/06/setting-up-dropbox-in-xubuntu.html](http://mangel312.blogspot.com/2014/06/setting-up-dropbox-in-xubuntu.html)
That link refers to an older version of Dropbox. The new qt5 version (3.0.3 for me) seems to be giving quite a few users, across distros, trouble.

The nature of the trouble seems to vary: a b/w icon in the systray, no icon in the systray, icon background not transparent, dropbox somehow messing with the systray, dropbox itself not running, etc. In my case, Dropbox (installed directly from dropbox.com using their "server script" on Lubuntu 14.04 without any dropbox-related software from Canonical repos or ppa) gave me the b/w icon and messed with my systray (tint2).

---

### Post by bashiergui on 2014-12-30
Sounds like it's time to file a bug report with Dropbox. I didn't find where to file it except to submit a support request.

---

### Post by vasa1 on 2014-12-30
> **bashiergui said:**
> Sounds like it's time to file a bug report with Dropbox. I didn't find where to file it except to submit a support request.If you're using the free version, you may get a boiler-plate response. I did ;)

Really, the issues seem so varied that I'm wondering how they released 3.0.3 as stable. It may just be that the (Linux) user base willing to test pre-release versions wasn't large enough.

For my minimal purposes, just backup, I've sorted things out by playing with the order in which things load at or just after log in. I have a tint2 panel on the RHS and a simple Conky on the LHS, both in the same row at the top of my screen.
I moved the png icons of my choice to /home/vasa1/.dropbox-dist/dropbox-lnx.x86_64-3.0.3/images. SVG images don't seem to work for me anymore. I suspect I'll need to do this each time the version number changes.
In terms of autostart, I have tint2 first and then a simple Compton.
After that I run **/home/vasa1/.dropbox-dist/dropboxd & exit** from a terminal. The dropbox icon doesn't appear at this point.
I restart tint2 and the icon appears as I like it and is functional for my limited needs. The dropdown menu doesn't obey my gtk theme although this is supposed to be automatic in qt5 with no need for qt-config. But I and others don't see that.
Then I start my Conky.
Bit laborious but it works for me: Openbox session in Lubuntu 14.04.

---

### Post by bapoumba on 2014-12-30
Well, nautilus-dropbox here on lubuntu 14.10. Last update (3.0.3) had the dropbox icon missing from the panel and dropbox not starting upon booting up. I manually added dropbox to the Autostart LXSession Applications (although already checked and a config file present in /home/bapoumba/.config/autostart), and it has been working since..

---

### Post by sorokin-nbt on 2014-12-30
Thanks a lot guys for taking your time replying to this issue!

**@**bapoumba
In my case dropbox does run and is listed in my start-up applications, I'm able to confirm that by running [FONT=courier new]dropbox status, [/FONT]it just simply won't show up until I restart it once or twice. I tried to work around it by creating a little bash script to restart dropbox 2 minutes after boot up, however that didn't quite work out.

---

### Post by vasa1 on 2015-01-02
> **bashiergui said:**
> Sounds like it's time to file a bug report with Dropbox. I didn't find where to file it except to submit a support request.
[https://bugreports.qt-project.org/browse/QTBUG-31762?focusedCommentId=268872&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-268872](https://bugreports.qt-project.org/browse/QTBUG-31762?focusedCommentId=268872&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-268872)

---

### Post by bashiergui on 2015-01-03
> **vasa1 said:**
> [https://bugreports.qt-project.org/browse/QTBUG-31762?focusedCommentId=268872&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-268872](https://bugreports.qt-project.org/browse/QTBUG-31762?focusedCommentId=268872&page=com.atlassian.jira.plugin.system.issuetabpanels:comment-tabpanel#comment-268872)Too bad, the big has been unresolved for more than a year. I did find this comment to be the most accurate IMO as far as when to expect a resolution:

"[Kovid Goyal]("https://bugreports.qt-project.org/secure/ViewProfile.jspa?name=kovid") added a comment - 03/Sep/14 10:30 AMI've also found some mailing list threads indicating that GNOME... is implementing its own version, and I have no idea what KDE is doing. Not to mention all the various "light" window managers. I suppose all this will coalesce into something that can actually be developed against whenever the year of the Linux Desktop finally arrives [IMG]https://bugreports.qt-project.org/images/icons/emoticons/smile.gif[/IMG]"



So any day then! ;)

---

