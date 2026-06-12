---
title: "TeamViewer install borked, can't seem to fix"
date: 2019-03-21
forum: General Help
---

### Post by sremick on 2019-03-21
Xubuntu 18.10

So the other day I went to run TeamViewer and found it was gone. So I tried to re-install it and this happens:

```
$ sudo apt install teamviewer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 teamviewer : Depends: libqt5qml5 (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
              Depends: libqt5quick5 (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
              Depends: libqt5webkit5 (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
              Depends: qml-module-qtquick2 (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
              Depends: qml-module-qtquick-controls (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
              Depends: qml-module-qtquick-dialogs (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
              Depends: qml-module-qtquick-window2 (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
              Depends: qml-module-qtquick-layouts (>= 5.5) but it is not going to be installed or
                       qt56-teamviewer but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

I've tried a few things:

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
```

I've also tried Synaptic to install qt56-teamviewer, but that fails too and just says it's "broken".

I suspect a non-standard PPA repository, but any useful way to determine which one so I just fix this problem without causing other problems (such as blowing away the entire sources.list and replacing with default)? I noticed a lot of the sources have "bionic" in them even though I'm on cosmic. Should I change all references to "bionic" to "cosmic" instead?

---

### Post by beankylla on 2019-03-22
Going in your software manager GUI might be an easier way to see what is happening.

Start synaptic or any other software manager and check out what sources you have available.

I would remove anything but the basic ubuntu sources and try again. 

This unless you have some kind of exotical software or setup?

---

### Post by sremick on 2019-03-22
This can be marked as solved. The issue turned out to result from some PPAs (not ones I had manually added, but automatic/default ones) that were still harcoded for bionic even though I was on cosmic. Something didn't upgrade properly. I went through and changed all the references, then went through upgrading everything and things are happy now, including Teamviewer.

---

### Post by slickymaster on 2019-03-22
> **sremick said:**
> This can be marked as solved. The issue turned out to result from some PPAs (not ones I had manually added, but automatic/default ones) that were still harcoded for bionic even though I was on cosmic. Something didn't upgrade properly. I went through and changed all the references, then went through upgrading everything and things are happy now, including Teamviewer.

See [here]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads") how you can mark your threads as solved.

---

