---
title: "Where are the program menus in Ubuntu 16.04 LTS?"
date: 2016-11-25
forum: General Help
---

### Post by loungehake on 2016-11-25
The program/application menus are so well hidden in Ubuntu 16.04 LTS that I ask myself if they really exist. It limits my use of Ubuntu to using the Chromium and Firefox web browsers.  I have also found a peculiarity which is that clicking the 'Ubuntu Software' item in the left hand menu bar on the desktop starts the associated application but it then closes itself after about 8 seconds of unresponsiveness.

Ubuntu 16.04 LTS is very disappointing after using Ubuntu 14.04 LTS. It is also less lively in performance.

I use the 32-bit version and updated from 14.04 to 16.04. I have only installed software via Ubuntu and only the firewall application and the Chromium browser at that.

---

### Post by ajgreeny on 2016-11-25
You should see most, but not all, I think, program menus in the top panel of Ubuntu with unity once your cursor moves into the top panel.

I do not use Ubuntu or unity by default but in the VM I have of 16.04 in VBox I do not see any obvious differences in this behaviour from 14.04.

In system settings have you set the menus to appear in the top window decoration of applications or have you left things as they are by default?

---

### Post by fenrice on 2016-11-25
I never cared much for unity, and use kubuntu because I like for everything to be out in the open about what is installed and available. Unity seems to work more from the paradigm of simplicity and you kind of just open the unity launcher with the "windows key" and start typing and assuming you know the name of the program you're looking for it will find it. That's great if you've been around linux for years but not so great if you aren't an old timer. Chances are google will help you find what you need in that case and you can find your program with the "windows key" method, and if not available just open up software and install. It's a different paradigm but it can work, and I gave it a shot, but I'm back to kubuntu, as I like the prearranged "folders of apps" idea, and not the "flat interface" of unity. I much prefer to sort my apps into logical categories in a launcher menu.

---

### Post by bearlake on 2016-11-25
For the last part of your question. Ubuntu Software has a bug in it at this time.

Use Synaptic Package Manager.

From terminal:

```
sudo apt install synaptic
```

```
sudo apt install apt-xapian-index
```

---

### Post by loungehake on 2016-11-26
I clean installed Ubuntu 16.06 LTS (64bit) today, 26 November 2016. Gnome Software Center is not to be found and Ubuntu Software Center is unusable. How can I use Ubuntu when I cannot install software?

This is the issue I was having with the 32-bit version which originally prompted this thread. I thought that a clean install would solve the problem but the result is disappointment. How do I install software from Ubuntu without the Ubuntu Software Center? The system is as installed plus the post installation updates. I have done nothing else with it.

Because I had been able to use the Ubuntu Software Center since I installed Ubuntu 16.04 LTS (32bit) over Ubuntu 14.04 LTS in late July, it causes me think that a bug must have been introduced fairly recently. I think that the Ubuntu Software Center was usable before recent updates were installed. I don't often use the Software Center so I can't remember when I last used it and therefore do not know when the problem was imported. You don't expect something like this to happen. I am amazed that the developers have not picked up on it.

Is there a fix or workaround available?

---

### Post by verymadpip on 2016-11-26
Hi there.
I recently had an issue with gnome software crashing. I believe it's installed by default in 16.04 rather than Ubuntu Software centre (center? /shivers at spelling).
I resolved my issue by running:
```
sudo apt-get update
sudo apt-get upgrade
```
from a terminal.

Good luck

---

### Post by ajgreeny on 2016-11-26
> **loungehake said:**
> I clean installed Ubuntu 16.06 LTS (64bit) today, 26 November 2016. Gnome Software Center is not to be found and Ubuntu Software Center is unusable. How can I use Ubuntu when I cannot install software?

This is the issue I was having with the 32-bit version which originally prompted this thread. I thought that a clean install would solve the problem but the result is disappointment. How do I install software from Ubuntu without the Ubuntu Software Center? The system is as installed plus the post installation updates. I have done nothing else with it.

Because I had been able to use the Ubuntu Software Center since I installed Ubuntu 16.04 LTS (32bit) over Ubuntu 14.04 LTS in late July, it causes me think that a bug must have been introduced fairly recently. I think that the Ubuntu Software Center was usable before recent updates were installed. I don't often use the Software Center so I can't remember when I last used it and therefore do not know when the problem was imported. You don't expect something like this to happen. I am amazed that the developers have not picked up on it.

Is there a fix or workaround available?
As bearlake says in post #4, install and use **synaptic** instead of **ubuntu software**,; it was the default package manager of Ubuntu for many years, as it still is in Debian, I think, and has always been my choice of GUI package manager, when I use a GUI.

---

### Post by loungehake on 2016-11-26
I reinstalled UBUNTU 16.04 LTS (64bit) **AGAIN**. This time I made sure that I installed the two extra programs I needed **BEFORE** updating Ubuntu. The Ubuntu Software Center worked before the updates were installed but not after. It has resumed the unwanted behaviour of disappearing after being displayed (without graphics) for a few seconds.

I am content. I guess that the problem will be identified and put right in due course.

There was no apparent option to install Synaptic on the DVD which I burned the installation package to after I downloaded the Ubuntu 16.04 LTS (64bit) ISO.
Is it actually the Synaptic software that is exhibiting the problem?

---

### Post by bearlake on 2016-11-26
Hold down the "Ctrl" + "Shift" keys and tap the Capital "T" and that will bring up the "Terminal Window" and enter the commands from post #4 one at a time.

---

### Post by loungehake on 2016-12-01
This issue is no longer a problem for me.  Thanks for the helpful information guys.

---

