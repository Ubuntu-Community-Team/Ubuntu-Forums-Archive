---
title: "firefox &amp; mplayer plugin problem"
date: 2006-12-08
forum: General Help
---

### Post by v4169sgr on 2006-12-08
Dapper user, firefox 1.5.0.8

I am having the problem described here:

[http://www.linuxquestions.org/questions/showthread.php?t=455805](http://www.linuxquestions.org/questions/showthread.php?t=455805)

i.e. something happened in the past week or so which has contributed to rather too much lost sleep ;(

The problem [cycling without playing the video stream] seems to happen MOST of the time when trying to play wmv streams e.g. the bbc news site, though on rare occasions this will work. Realplay streams are not affected.

Running firefox from the shell allows these errors to be seen [two lines per cycle]:

```


(Gecko:9451): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(Gecko:9451): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed


```

I've tried the following so far:

* Run in -safe-mode;

* Run as a different user, and as root [with -H];

* Moved ~/.mozilla out of the way;

* Downloaded firefox 2.0 as a standalone tar ball and copied the plugins over;

* Uninstalled / reinstalled the firefox mplayer plugin package;

None have worked to date.

Here is the contents of /var/cache/apt/archive for this month, as I am sure everything worked fine before:


```


  60 -rw-r--r-- 1 root root   56360 2006-12-01 16:03 liblircclient0_0.8.0-9ubuntu1~dapper1_i386.deb
1336 -rw-r--r-- 1 root root 1360320 2006-12-01 16:03 kino_0.92-1ubuntu2~dapper1_i386.deb
  16 -rw-r--r-- 1 root root   13190 2006-12-02 07:03 flashplugin-nonfree_9.0.21.78.2ubuntu1~dapper1_i386.deb
  44 -rw-r--r-- 1 root root   44520 2006-12-04 21:04 libgsf-1-common_1.13.99-0ubuntu2.1_all.deb
2872 -rw-r--r-- 1 root root 2934258 2006-12-04 21:04 libxine-main1_1.1.1+ubuntu2-7.5_i386.deb
 124 -rw-r--r-- 1 root root  121370 2006-12-04 21:04 libgsf-1-113_1.13.99-0ubuntu2.1_i386.deb
 684 -rw-r--r-- 1 root root  692882 2006-12-06 03:03 evince_0.5.2-0ubuntu3.2_i386.deb
 964 -rw-r--r-- 1 root root  981652 2006-12-07 02:06 gnupg_1.4.2.2-1ubuntu2.4_i386.deb


```

The problem *might* have been something to do with the kino update, as I have been using Automatix, and it is possible that a repo conflict could have arisen between official dapper and automatix, but I doubt it from the context of the link at the top.

At the moment, I am using the MediaPlayerConnectivity expension in firefox v 1.5 to work around the issue. However, this is just not as nice ... ;(

Has anyone managed to solve this problem?

---

### Post by scourge on 2006-12-09
I had the same issue in Edgy, but not in Dapper. I solved it by adding the line "noembed=1" to ~/.mplayer/mplayerplug-in.conf. It makes the videos appear in a separate window, which is fine by me because I want to watch them in full screen anyway. Another way that works is to use x11 or gl as video output and oss as the audio output, but then the powerful video processor of my graphics card is not used and HD videos slow to a crawl.

If you really want to find out what's causing the problem, add the line "debug=1" to the config file and you'll get plenty of data to read through.

---

### Post by v4169sgr on 2006-12-09
Thank you Scourge, I'll try that next time I get the chance. It really puzzles me though that this issue has been known for at least five months [since July this year], is a showstopper for mwv video streaming in firefox with mplayer, and no obvious fix is apparently available. Any other comments?

---

