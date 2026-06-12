---
title: "Getting the most out of Ubuntu (12.04)"
date: 2013-11-19
forum: General Help
---

### Post by ballistic turtle on 2013-11-19
I'm currently on 12.04 alongside Windows 7. I like Ubuntu and how it does things different and actually makes my screen look closer to how I want it and pushes it harder than Windows seems to (although, clarity, Windows wins by a bit, but Ubuntu has high brightness and better resolution if that makes sense. In any case, the screen looks more Mac-like whereas Windows seems to make it look a bit washed out, but enough of that), but when I go into Ubuntu it seems a bit empty, none of the programs I use are there (I haven't installed any, but hopefully you understand what I mean) and it seems a bit empty. I get that, what do I do now feeling.

So, what do I do now? What do I do to Ubuntu to make it more the OS I want to use? Also, call me paranoid, but what can I do about antivirus?

---

### Post by Allavona on 2013-11-19
Ok. Antivirus=NONE. There are companies that make Antivirus programs for Linux. Avast and Comodo, to name a couple.  But most of these are geared towards making sure that files you may share with windows are not infected and for web protection to steer you clear of malicious sites. And just like in Windows, will use an absurd amount of resources to do so. File and storage permissions within Linux make it difficult for malicious programs like viruses to work in Linux. So IMHO, they are uneeded. If your going to share with Windows, save to a usb drive and scan it from within Windows before moving the file(s) to the file system.

As for Ubuntu feeling empty, that may be due to the fact that the desktop is not cluttered with shortcuts and all the bloatware that OEM manufacturers include on their systems. Ubuntu and Linux in general are barebones installs only including what you need to get going. The rest is up to you. The software center is chock full of good things for you to install and play with.

And as for the screen, depending on your graphics, you may be able to install your proprietary drivers instead of the open source ones. Check out Additional Drivers for this.

---

### Post by ballistic turtle on 2013-11-19
> **Allavona said:**
> Ok. Antivirus=NONE. There are companies that make Antivirus programs for Linux. Avast and Comodo, to name a couple.  But most of these are geared towards making sure that files you may share with windows are not infected and for web protection to steer you clear of malicious sites. And just like in Windows, will use an absurd amount of resources to do so. File and storage permissions within Linux make it difficult for malicious programs like viruses to work in Linux. So IMHO, they are uneeded. If your going to share with Windows, save to a usb drive and scan it from within Windows before moving the file(s) to the file system.

As for Ubuntu feeling empty, that may be due to the fact that the desktop is not cluttered with shortcuts and all the bloatware that OEM manufacturers include on their systems. Ubuntu and Linux in general are barebones installs only including what you need to get going. The rest is up to you. The software center is chock full of good things for you to install and play with.

And as for the screen, depending on your graphics, you may be able to install your proprietary drivers instead of the open source ones. Check out Additional Drivers for this.

My update manager is broken, still waiting for a fix for that, so don't know how I'd do it O_o

---

### Post by tgalati4 on 2013-11-20
Open a terminal and post the output of:

```
sudo apt-get check
```

---

