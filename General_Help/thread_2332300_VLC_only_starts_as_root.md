---
title: "VLC only starts as root"
date: 2016-07-30
forum: General Help
---

### Post by Charlotte18 on 2016-07-30
When I start vlc as a normal user, I get the error "Segmentation fault (core dumped)." 

If I start vlc with "sudo vlc-wrapper," it opens properly.

Any ideas?

---

### Post by Charlotte18 on 2016-07-30
I should have mentioned above that I've already purged and reinstalled VLC. I've deleted the VLC folder from .config, and I've tried the VLC daily build. Same problem persists. When I start vlc as a normal user, I get the error "Segmentation fault (core dumped)." If I start vlc with "sudo vlc-wrapper," it opens properly.

---

### Post by gordintoronto on 2016-07-30
What version of Linux are you using? (eg. Lubuntu 16.04 64-bit) How did you install VLC? Version? VLC is my primary media player, and I'm currently using 2.2.2.

---

### Post by Charlotte18 on 2016-07-30
I'm using Ubuntu 16.04 64 bit, and I installed VLC by typing "sudo aptitude -v install vlc." I do not know the version number which was installed then, but it was whatever version is in the official Ubuntu repositories. 

Then, I installed the version from the Ubuntu Daily PPA (3.0, I think), but I had the same problem.

The weird thing here is that VLC will run properly if I type "sudo vlc-wrapper" in the terminal. If I just type vlc, I get the error: "Segmentation fault (core dumped)." 

So I'm thinking, "permissions error"?

---

### Post by gordintoronto on 2016-07-31
I think the "Ubuntu Daily PPA" contains pre-release software for the next version of Ubuntu. If you have enabled that PPA, you're running unstable software, which should be expected to break. Sorry, I don't go there.

---

### Post by Charlotte18 on 2016-08-01
I tried the version from Viedolan's daily releases because the official Ubuntu version from the 16.04 repository stopped working and demonstrated the problem I described in the original post. The version from the daily releases demonstrated the same problem, but it is not possible that using the daily repository caused the problem because in the sequence of events, it was not active when the problem first occurred.

I only used the daily version of VLC when the other steps did not solve the problem (e.g., purging and reinstalling, deleting VLC's .config folder, etc.).

---

### Post by mc4man on 2016-08-01
segfaults are hard to deal with as little info.

i'd first try creating a new user, log in to that user & see if vlc opens.
Also a segfault should produce a crash report in /var/crash/ , if there right click on > Open with Report ... > Show Details. There may be some small tidbits in 'Title' & 'Stacktrace Top'

---

### Post by Charlotte18 on 2016-08-01
VLC also demonstrates the same error under a newly-created user. 

The error report's "Title" field reads "vlc crashed with SIGSEGV in QFont::QFont()." 

The "Stactracetop" reads:

 QFont::QFont(QFont const&) () from /usr/lib/x86_64-linux-gnu/libQt5Gui.so.5
 QApplicationPrivate::initializeWidgetFontHash() () from /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5
 QApplicationPrivate::construct() () from /usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5
 ?? () from /usr/lib/vlc/plugins/gui/libqt4_plugin.so
 start_thread (arg=0x7fea88192700) at pthread_create.c:333

I can only guess that there's a problem with fonts in qt, but I'm not well-versed enough in reading these error reports. The "Package" filed shows "vlc-nox 2.2.2-5."

---

### Post by mc4man on 2016-08-01
No clue, never seen this before. Just to ck. if you've somehow got the gles version installed what's this report? - 
```
apt-cache policy libqt5gui5* 
```

---

### Post by Charlotte18 on 2016-08-01
I don't think so:

libqt5gui5:
  Installed: 5.5.1+dfsg-16ubuntu7.1
  Candidate: 5.5.1+dfsg-16ubuntu7.1
  Version table:
 *** 5.5.1+dfsg-16ubuntu7.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     5.5.1+dfsg-16ubuntu7 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/main amd64 Packages
libqt5gui5-gles:
  Installed: (none)
  Candidate: 5.5.1+dfsg-16ubuntu6
  Version table:
     5.5.1+dfsg-16ubuntu6 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages

But why does "sudo vlc-wrapper" open vlc properly? Why is that? Without "sudo," "vlc-wrapper" gives the segmentation fault error.

---

