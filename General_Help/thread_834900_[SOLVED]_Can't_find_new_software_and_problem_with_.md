---
title: "[SOLVED] Can't find new software and problem with flash and sound"
date: 2008-06-19
forum: General Help
---

### Post by mmellado on 2008-06-19
Hi people.

Im working on Ubuntu Hardy Heron, iv been updating everything since the release. In the beginning everything was working fine for me, but lately iv noticed some bugs for which i don't know the reasons.

Bug #1: I use emesene for msn chat, but lately iv saw some people using mercury, so i tried to install it. When i did so, i noticed that i couldn't find the icon in the applications menu. I thought it might be an installation error, so i added mercury to the sources list following a guide in the mercury messenger page and installed it via apt-get install. For my surprise, exactly the same thing happened, the program seemed to be installed but it couldn't be found in the applications menu. Then i thought it was a problem with mercury, but then i tried to do a new experiment. I tried to install epiphany browser just for testing, and the same thing happened. program was installed and i was even able to run it via the terminal with the command but i couldn't find the icon in the menu. I was not able to try and run mercury tough, since i don't know its command. Now i know i can run my new programs from the terminal with their commands, but i would prefer to be able to see them in the menu and solve this problem.

Bug #2: iv noticed that after i see videos in flash format (like youtube videos), when i close them, i cant hear any more sound in my computer until i reset. I thought it might be a problem with my sound card (don't really know the model, but my laptop is an hp pavilion dv6646us) but then i realized that a friend using a dell computer had the exact same problem with his sound, and i don't really know what to do about this.

Can someone give me any advice please??

---

### Post by mmellado on 2008-06-19
My Bad I Marked Xubuntu But Its Ubuntu!!!

---

### Post by iaculallad on 2008-06-19
> **mmellado said:**
> Hi people.
Bug #2: iv noticed that after i see videos in flash format (like youtube videos), when i close them, i cant hear any more sound in my computer until i reset. I thought it might be a problem with my sound card (don't really know the model, but my laptop is an hp pavilion dv6646us) but then i realized that a friend using a dell computer had the exact same problem with his sound, and i don't really know what to do about this.

Try to install the libflashsupport file

```
sudo apt-get install libflashsupport
```

---

### Post by Happy_Man on 2008-06-19
In response to issue 2: This is a problem with PulseAudio, Ubuntu's brand new sound engine. To fix these issues and then some that you may or may not be experiencing, see here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Please never install libflashsupport, as it is a tremendous waste of time. It may help, but it exposes a bug in Flash that causes to crash frequently, taking down your current browser session with it.

---

### Post by mmellado on 2008-06-19
about to try both options, ill give my feedback in a minute

---

### Post by mmellado on 2008-06-19
> **iaculallad said:**
> Try to install the libflashsupport file

```
sudo apt-get install libflashsupport
```

I did it now, everything seems to be working fine now =) now i hope i can get feedback on issue number 1

> **Happy_Man said:**
> In response to issue 2: This is a problem with PulseAudio, Ubuntu's brand new sound engine. To fix these issues and then some that you may or may not be experiencing, see here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

Please never install libflashsupport, as it is a tremendous waste of time. It may help, but it exposes a bug in Flash that causes to crash frequently, taking down your current browser session with it.

Thanks for the link, im going to try all the others =)

---

### Post by cariboo on 2008-06-19
If a progran doesn't show up in the Application menu, you can always add it manually. Just right click on Applications then click Edit Menus, pick the section yu want to add an application to, then click the New Item button. A window will pop up called Create Launcher fill in the name of the program then in the command line enter the command to run your program, if you don't know the command you need, click the browse button, in the window that opens, you will see  in the left pane filesystem, double click it then navigate to /usr/bin this is where most of the programs are installed. On my computer /usr/bin has over 1500 programs listed so it make take a bit of time to locate what you want. After you have done this enter a comment if you want, then click OK

---

### Post by iaculallad on 2008-06-19
> **mmellado said:**
> 
Bug #1: I use emesene for msn chat, but lately iv saw some people using mercury, so i tried to install it. When i did so, i noticed that i couldn't find the icon in the applications menu. I thought it might be an installation error, so i added mercury to the sources list following a guide in the mercury messenger page and installed it via apt-get install. For my surprise, exactly the same thing happened, the program seemed to be installed but it couldn't be found in the applications menu. Then i thought it was a problem with mercury, but then i tried to do a new experiment. I tried to install epiphany browser just for testing, and the same thing happened. program was installed and i was even able to run it via the terminal with the command but i couldn't find the icon in the menu. I was not able to try and run mercury tough, since i don't know its command. Now i know i can run my new programs from the terminal with their commands, but i would prefer to be able to see them in the menu and solve this problem.


Perform a manual installation if it would work:

-Download [Mercury's deb file]("http://surfnet.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb").

-Assuming that you had successfully completed the download, issue the following commands on your terminal:

```
cd ~/Desktop
sudo dpkg -i mercury-messenger_1710_S7_i386.deb
```

Then try to locate your Mercury icon on Applications->Internet.

-

---

### Post by mmellado on 2008-06-19
> **cariboo907 said:**
> If a progran doesn't show up in the Application menu, you can always add it manually. Just right click on Applications then click Edit Menus, pick the section yu want to add an application to, then click the New Item button. A window will pop up called Create Launcher fill in the name of the program then in the command line enter the command to run your program, if you don't know the command you need, click the browse button, in the window that opens, you will see  in the left pane filesystem, double click it then navigate to /usr/bin this is where most of the programs are installed. On my computer /usr/bin has over 1500 programs listed so it make take a bit of time to locate what you want. After you have done this enter a comment if you want, then click OK

Let me try this then, i will need to reinstall mercury to test it

Weird. i just rechecked my applications Menu... epiphany is now there, but after i reinstalled mercury'messenger it keeps not appearing. Ill try to manually add it

---

### Post by mmellado on 2008-06-19
> **iaculallad said:**
> Perform a manual installation if it would work:

-Download [Mercury's deb file]("http://surfnet.dl.sourceforge.net/sourceforge/projeto-messias/mercury-messenger_1710_S7_i386.deb").

-Assuming that you had successfully completed the download, issue the following commands on your terminal:

```
cd ~/Desktop
sudo dpkg -i mercury-messenger_1710_S7_i386.deb
```

Then try to locate your Mercury icon on Applications->Internet.

-

Just did. Icon still doesnt appear =/

---

### Post by mmellado on 2008-06-19
ok weird thing happened, a popup appeared on my screen, i didnt read it or anything just closed it (my bad) but after that i checked my meny and mercury is now there... weird issue... thank you eveyrbody!!

---

