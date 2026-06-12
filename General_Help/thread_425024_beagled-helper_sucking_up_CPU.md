---
title: "beagled-helper sucking up CPU"
date: 2007-04-27
forum: General Help
---

### Post by shoofy on 2007-04-27
Since upgrading to Feisty, the process beagled-helper has been running non-stop at between 30%-50% CPU. beagle-status reports an empty queue. I tried deleting my .beagle folder and it didn't help. Does anyone know how I can make it work normally?

EDIT: (changed .beryl to .beagle)

---

### Post by Schalken on 2007-04-27
Deleting beryl configuration will not affect beagle. Novell is currently working on the problem of beagle's high and untimely CPU usage. To remove beagle temprorarily go to Preferences > Sessions and uncheck Beagle Search and Beagle Search Daemon. Relogin to make changes take effect. Recheck them to get them back. You can also remove beagle from the system completely with Synaptic, if you like.

---

### Post by shoofy on 2007-04-27
Sorry, that was a typo. I meant .beagle. I like beagle and I don't particularly want to disable it, unless there is a good alternative out there. If they are working on a fix I'm happy just to sit and wait for it.

---

### Post by Schalken on 2007-04-28
There is an alternative called Tracker, but it isn't as mature. It is said to be faster, though.

---

### Post by CocoAUS on 2007-04-28
I wouldn't recommend Tracker.  It might have more potential, but it's extremely unreliable at the moment.  I've tried switching 3 times now, but it just doesn't work right.  And it eats as much CPU as Beagle does sometimes.

---

### Post by nudeatom on 2007-05-09
I had this problem then I stopped Beagle trying to index my live torrent folder and the usage dropped right down.

---

### Post by dbera on 2007-05-10
Shoofy, if you follow it up on the beagle mailing list or irc (the addresses are on [http://beagle-project.org](http://beagle-project.org)) they will be able to help you. They will invariably ask you for beagle log files located at <HOME>/.beagle/Log so have them ready.

---

### Post by jamiemcc on 2007-05-13
> **CocoAUS said:**
> I wouldn't recommend Tracker.  It might have more potential, but it's extremely unreliable at the moment.  I've tried switching 3 times now, but it just doesn't work right.  And it eats as much CPU as Beagle does sometimes.

This should not be the case. The ubuntu devs have been assessing tracker (the 0,5,4 version in the fiesty repo) as well as beagle and they have unanimously decided to integrate tracker by default in Gutsy main.

Their reasons are simply because tracker runs really well on low end hardware and generally does not consume excessive resources or CPU and hence does not slow the system down significantly. Whilst the initial index can take some CPU, it is in most cases for a very short time (tracker indexes at approx 100 text files per second so the initial index is created often in minutes and even big hard drives should not take more than an hour or so)

Nevertheless If you are experiencing problems then pls file bugs.

---

### Post by jordilin on 2007-05-15
Not only Beagle sucks your CPU, in my case eats my whole RAM resources. In *EVERY* Ubuntu release there are PROBLEMS with BEAGLE. I don't know who is to blame for this, either Novell or Ubuntu, but it is a great pity having to turn off this great application because it eats your whole resources. :frown:

---

### Post by Kuoi on 2007-05-15
I was sick after I had to reboot my computer again , when I don't touched it for about a half an hour.
Every time I came back , I was hoping Beagle was not bussy indexing.
When it was , I had to reboot , because it was eating all my memory , and the cpu was at 100%
That's why I've uninstalled it 'completely' with Synaptic.

Now I use Tracker , but can somebody tell me how i can configure it ?
I don't see it indexing much for the moment , not that I care of , but for the moment I can't find many.

Kuoi

---

### Post by jordilin on 2007-05-15
Beagle in Ubuntu sucks big time. I don't know what happens in distros such as SUSE, anyone using SUSE and Beagle?

---

### Post by engla on 2007-05-19
As usual, try the alternative [tracker]("http://www.gnome.org/projects/tracker/") if beagle doesn't work. Tracker is in the repositories in Ubuntu 7.04, but it also works if you install it yourself in 6.10

Tracker is configured at the moment by editing the configuration file at ~/.Tracker/tracker.cfg (a pretty well commented file so it should not be that hard)

---

### Post by shoofy on 2007-05-20
I can't get Tracker to index my documents directory. I have a partition with all my documents mounted at /doc and I adusted tracker.cfg to

WatchDirectoryRoots=/docs;/home/******;

but it only indexes my home directory even after restarting tracker.

---

### Post by PartisanEntity on 2007-05-20
> **Kuoi said:**
> 
Now I use Tracker , but can somebody tell me how i can configure it ?


```
~/.Tracker/tracker.cfg
```

---

