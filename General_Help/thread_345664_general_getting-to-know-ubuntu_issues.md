---
title: "general getting-to-know-ubuntu issues"
date: 2007-01-24
forum: General Help
---

### Post by maclenin on 2007-01-24
I have recently installed edgy eft (2.6.17-10-generic, without windows) on a Dell Inspiron 600m and am encountering issues that I thought I'd chronicle here - with the aim of trying to understand the issues, resolve them (if they are resolveable) and pass along any knowledge that might be useful to others who stumble across this thread....

So, without further ado:

**A. Terminal freezes when running applications from the command line:**

[COLOR="Lime"]**[]**[/COLOR] = terminal cursor
```
ubuntu@ubuntu:~$ firefox
[COLOR="Lime"]**[]**[/COLOR]
```

When I run an applicaiton from the command line, the terminal freezes (i.e. the command line does not "re-set" after the application opens, as shown above) and stays frozen until either the terminal or the application, is closed...ergo: if the terminal is the first to be closed, the application will close with the terminal; if the application is the first to be closed, the command line will reset to:

```
ubuntu@ubuntu:~$ firefox
ubuntu@ubuntu:~$ [COLOR="Lime"]**[]**[/COLOR]
```

Previously, I'd been able to open multiple windows / tabs in firefox via the terminal - and perform other tasks in that same terminal window while both the terminal and firefox were open - and could then close both, independently. In this current "frozen state", I am able to use the application (e.g. firefox) without issue - but the terminal (as mentioned) remains frozen (until either the terminal, itself, or the application are closed)...it strikes me as a troubling connectedness....

**B. sudo modprobe -r bcm43xx**

I ran the **sudo modprobe -r bcm43xx **command while troubleshooting my wireless configuration - and when I rebooted and ran **lsmod**, I found that bcm43xx was still on the list of modules...i.e. had not been "removed" as I thought was supposed to happen when using this command. Am I missing something?

**C. Missing icons**

After booting with a USB drive (WD Passport) connected (not as a boot drive), I noticed that the ubuntu "Applications" and "Recycle Bin" icons had vanished from my desktop.... When I reboot the machine with the USB drive disconnected, the icons are still missing - in the meantime, I have been able to + Add the missing icons back to the desktop panels, however, the fact that they vanished without my explicit order, causes me to worry....

Note: The drive mounted via pmount - there is no listing of the USB drive in fstab and I found this file: /media/WD Passport/.created_by_pmount - and I am wondering whether the pmount process is somehow behind the missing icons.

---

### Post by llamakc on 2007-01-24
A. Run the command with an ampersand after it:

firefox &

and you'll get your prompt back.

---

### Post by matthewstory on 2007-01-24
yeah, i can only respond to A and B,

A. That's the standard behavior of every linux distro i've ever run, I'd rec. the same thing as the last guy, run it in the background with the ampersand, or suppress the output to the null shell:

firefox &> /dev/null

The behavior for this is supposed to keep the terminal window open and print the STDOUT and STDERR to the window.  You could do the things above, or just open a new terminal tab if you are so inclined SHFT+CTRL+T.

B. modprobe -r will remove the module from the kernel, but it won't actually remove the module from the list, as I understand it.  If you want a little more comprehensive program for LKMs use modconf, and run it without any options, this will give you a curses interface that allows you to more easily explore all the modules.  

C. This would concern me too.

---

### Post by maclenin on 2007-01-24
Thanks for the input, folks.... I distinctly remember being able to load a couple of web sites - one after the other via the terminal (maybe it was while I was running off LiveCD - with slightly different rules)...anyway - I appreciate the clarifications.... I consider A. and B. [SOLVED]

So, I leave C. in play:

**C. Missing icons**

After booting with a USB drive (WD Passport) connected (not as a boot drive), I noticed that the ubuntu "Applications" and "Recycle Bin" icons had vanished from my desktop.... When I reboot the machine with the USB drive disconnected, the icons are still missing - in the meantime, I have been able to + Add the missing icons back to the desktop panels, however, the fact that they vanished without my explicit order, causes me to worry....

Note: The drive mounted via pmount - there is no listing of the USB drive in fstab and I found this file: /media/WD Passport/.created_by_pmont - and I am wondering whether the pmount process is somehow behind the missing icons.

For Additional Reference: Click [here]("http://ubuntuforums.org/showthread.php?t=344234")....

---

### Post by maclenin on 2007-01-29
Had to "hard shut-down" after the DVD drive froze on a commercial DVD - and icons have begun to disappear, once again (after re-start).... As this install or the software, itself, strike me as a tad fragile, I am probably going to do end up doing a re-install from a newly-created AlternateCD.... However, should anyone have any insights re: missing icons and their possible connection to pmount or hard shutdowns - or have other remedial suggestions short of a re-install, please post a word!

---

### Post by allwin on 2007-01-29
> **maclenin said:**
> Had to "hard shut-down" after the DVD drive froze on a commercial DVD - and icons have begun to disappear, once again (after re-start).... As this install or the software, itself, strike me as a tad fragile, I am probably going to do end up doing a re-install from a newly-created AlternateCD.... However, should anyone have any insights re: missing icons and their possible connection to pmount or hard shutdowns - or have other remedial suggestions short of a re-install, please post a word!

I'm a n00bie, too, but I can confirm that, unlike some other popular OS'es, GNOME "forgets" its desktop settings at random LOTS of times for no apparent (to me) reason.  Like for example, the order of things in the panels might change between logins or boots.  Or Nautilus might just launch itself two or three times without a click upon login.  I too went through a clean install thinking I did something, only to have the same phantom things re-appear.

I think GNOME asks you to redefine the notion of stability, IMHO.  If you run a program called GCONF-EDITOR, you can get some further insight as to what's under the covers of desktop settings besides the little applets you see in the GUI.  You CAN set things to lock down, apparently, the fluid choice must be the default for some strange reason.

Well, it's a server OS with a window kludge sitting on top...and why do you think they call it EDGY...you and I might be better served installing the older LTS version, seriously:)   I have this on two older PC's and for me, every boot and log in has been a crap shoot as to what could possibly happen next, in part because I have tried to install the latest available versions of eye candy and multimedia.  Just one person's anecdote, mind you.

---

### Post by maclenin on 2007-01-29
And a very fruitful anecdote, at that.... Thanks for the pearls. I will take a look "under the covers", as you recommend - to learn and, perhaps, to improve. It all makes one wonder what that feisty fawn will bring! Anyway, thanks for the insights. I'll be sure to post additional clues - left by those edgy efts - as I encounter them....

---

