---
title: "Logging in redirects back to the log in prompt"
date: 2020-08-15
forum: General Help
---

### Post by Dan_Bowser on 2020-08-15
Hello,

My PC boots normally to the log in screen. When I input my password the OS works a bit then loops back to the log in screen. It doesn't produce any additional output  or error messages so I have no idea why it won't let me through to the GUI. I'm using kubuntu 18.04 LTS. 

Just before the problem started a wine program was trying to update and appears to have used up all the space that was left on my OS drive. (IDK if the OS needs some kind of swap space on the drive to boot normally.) My guess is that this doesn't matter but I figured I should add in some info about what I was doing before the thing broke.

I have a flash drive with another version of kubuntu on it and I was able to boot into on the PC with the broken OS. It's kubuntu 20.04 LTS.

Before I do anything I want to copy files from the old OS drive onto a storage drive. I don't have access to root with the file manager (dolphin here.) I can't swap to my old user profile either when I try su - daniel it says the user doesn't exist and "sudo dolphin" gives an error message of "Executing Dolphin with sudo is not possible due to unfixable security vulnerabilities."

Can anyone tell me what to do to be able to copy these files I need to save?

Does anyone have advice for fixing/restoring the old OS? (I have a lot of programing software on the old OS that's difficult to set up and configure so I'd rather not reinstall everything.)

---

### Post by Impavidus on 2020-08-15
With a full hard drive, you cannot start a GUI session. When you login, the GUI session crashes at once and sends you back to the login screen. Otherwise the system works fine. You can use ctrl+alt+F1 to ctrl+alt+F7 to switch between multiple consoles, one of those (probably 1 or 7) has the GUI. There you can try to login on the command line interface and clear some disk space. You can also use the live session, which will give you a GUI, but makes it a bit harder to use the package manager. You can't su to your old user because that doesn't exist in the live session. You can access the filesystem of your installed system.

Is there a problem with sudo -H dolphin? I don't use dolphin. I use Xubuntu (and do file management from the terminal anyway). You can try a different filemanager or use the terminal.

A reinstall is really overkill in this case. I would even dig my live usb out of my drawer.

---

### Post by Dan_Bowser on 2020-08-15
sudo -H dolphin gives the same error.

OK. I know where the files are that are taking up the disk space (/home/daniel/Games/wargaming-game-center/) and I can just nuke the entire folder  One of the ctrl+alt+F# commands should get me to my old user account. For the remove command it's just

rm -R /home/daniel/Games/wargaming-game-center/

Is that right?

---

### Post by SeijiSensei on 2020-08-15
You can fix problems like these using "recovery mode:"  [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by Dan_Bowser on 2020-08-15
Ah sorry I already did the thing that I wrote out earlier.

I'm past the log in screen and it looks like the OS is functioning normally.

Thanks for the help

---

### Post by Impavidus on 2020-08-16
Great. Can you mark this thread as solved? Tread tools &#8594; mark as solved.

---

### Post by ActionParsnip on 2020-08-16
Also run:
```
 
sudo apt clean

```

---

