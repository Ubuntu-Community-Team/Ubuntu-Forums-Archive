---
title: "Nautilus bug? Double click opens multiple windows"
date: 2006-10-30
forum: General Help
---

### Post by NyquistLimit on 2006-10-30
I originally posted this in the edgy forums just before it closed and I'm still having the same problems so I thought I'd post it again in here, along with a few updates.

I've noticed this behaviour ever since upgrading from Dapper to Edgy. Sometimes when I double click on a video file in Nautilus it will create 2 instances of mplayer.

I've been testing this quite throroughly and it happens every 3rd time I double click the file. It seems kind of odd that this happens every third time. It's very consistent.

Are there any logs I can look at to find out whats happening? It doesn't happen with PCMan File Manager so I'm pretty sure it's a Nautilus bug.

Another problem affecting Gnome is when I click on a combobox while the mouse pointer is moving. This will instantly cause the menuitem under the mouse to be selected. Even if the mouse moves only one pixel while clicking on the combobox it will select the item. This is very frustrating sometimes because I have to keep my mouse completely still otherwise the combobox just appears and closes again within the blink of an eye.

I can reproduce this every single time by moving the mouse across a combo box and clicking on it. I don't really like having to hold down the mouse button while selecting things in a dropdown menu. I think Gnome thinks that because I've moved the mouse the menuitem beneath the cursor should be selected when I release the mouse button. Is there a way to disable the selection of menuitems on a mouse button release, because that would probably get rid of this problem for me.

I've only recently migrated from Windows over to Ubuntu (about 3 weeks ago) and so far I'm throughly impressed albeit with a few minor issues. There's a great community spirit here that helped alot in my decision to ditch windows.

I hope I've explained the problems in enough detail to be understood. Any help will be much appreciated!

---

### Post by onon_onon on 2006-11-01
I'm using Beryl as window manager and I have the same problem here, the double click opens multiple windows (really a lot), so I don't think it is a Nautilus issue. Fresh upgrade from Dapper to Edgy.

---

### Post by cmcginty on 2007-01-05
I'm on a fresh install (1 week old) of 6.1 and I also have seen this happen. Seems to be random at time.

---

### Post by orb9220 on 2007-01-07
It is a nautilus bug and been doing it for awhile. 

Sometimes when I logout then in nautilus will launch mutiples of itself even when it was not running when I loged out.

I have a gksudo icon on panel which when I click wil: Launch 5 instances,closes all of them then click again and it will launch 2 intances,close those and click icon again then I finally get 1.

On reboot's I have also have had the sessions manger or a term open up even tho they where not running when I shutdown.

This seems to happen in the 5-15% of the time going into gnome and beryl.

---

### Post by imatwork on 2007-01-08
I have the same problem, but more like orb9220. Nothing strange on reboot's though, and I do not use Beryl.

I have installed Edgy many times on the same system, and never noticed this until I decided to modify the hardware inside the case.

I **had** been running an SBLive, and an Intel 10/100.

This recent install (07Jan07) I replaced the Intel NIC with a DLink DFE530TX+, removed the SBLive, and enabled the onboard CMEDIA audio on my Asus P4B533 mobo.

NOTE: with the old configuration this problem never existed. it began after changing the hardware.

The issue could be coincidental for me. Its been about 2 weeks since the last install, and some update could also be causing this.

Have any of you made hardware changes as well?

Got similar hardware?

---

### Post by imatwork on 2007-01-09
Is it just the five of us with this problem?

---

### Post by orb9220 on 2007-01-09
Yes because I just remembered that I forgot to do my monthly 

"Sacrifice one virgin MS employee to the fires of Goddess Ubuntu"

No wonder I better get on that.

---

### Post by imatwork on 2007-01-09
> **orb9220 said:**
> Yes because I just remembered that I forgot to do my monthly 

"Sacrifice one virgin MS employee to the fires of Goddess Ubuntu"

No wonder I better get on that.

What does this have to do with the topic?

---

### Post by imatwork on 2007-01-10
I'm curious if there is an answer...

Bump ^

---

### Post by imatwork on 2007-01-11
Still curious.

Bump ^

:-k

---

### Post by deeek on 2007-01-17
I am having this exact bug and it is getting annoying.  Sometimes it opens up 9 windows when I go to the Home link in the places menu.  I hope there is a fix soon.

---

### Post by jaxson on 2007-01-17
I have the same bug also. It opens up 4 extra home nautulis windows at once, but it doesn't do it all the time :(

---

### Post by imatwork on 2007-01-23
Bump ^

---

### Post by imatwork on 2007-01-25
stayin alive...

---

### Post by allwin on 2007-01-25
Me too.  At first I thought I was too aggresively clicking.  But there are many times I log in and Nautilus launches itself multiple times for no reason.  Glad to see it's not my mousing skills or anything, and I'm not the only person getting this.  Clues anybody?

---

### Post by imatwork on 2007-01-29
This is probably a bug.

I reinstalled over the weekend, and the problem has gone away.

I did not put back in the SBLive, or the Intel NIC.

Strange...

:-k

---

### Post by Tachyon_ on 2007-01-29
I also confirm this bug, however, it's gone now, and I think it was because of custom made launchers.  First I also thought It was because of the speed I did the double click. It doesn't occur when I open a file or folder when nautilus is running, but it does when its not. For example, I couldn't find a simple way to make a shortcut without the arrow sign at top right corner, I made a custom shortcut with command "nautilus /media/usbdisk" for example. Now when I click it, I get 5-8 instances of nautilus, 4-6 of them at home folder. Do you also use the desktop launchers or does it also occur with clicking normal folder?

Now also my launchers work, I had to restart X (Ctrl+Alt+Del - closes all programs) because of crashing CSS, so that might be the solution, I haven't rebooted in two weeks, so did you try reboot or X restart in case of crashed and hidden instance of nautilus (it's running in my computer even thought no folders are open)?

---

### Post by imatwork on 2007-01-30
> **Tachyon_ said:**
> I also confirm this bug, however, it's gone now, and I think it was because of custom made launchers.  First I also thought It was because of the speed I did the double click. It doesn't occur when I open a file or folder when nautilus is running, but it does when its not. For example, I couldn't find a simple way to make a shortcut without the arrow sign at top right corner, I made a custom shortcut with command "nautilus /media/usbdisk" for example. Now when I click it, I get 5-8 instances of nautilus, 4-6 of them at home folder. Do you also use the desktop launchers or does it also occur with clicking normal folder?

Now also my launchers work, I had to restart X (Ctrl+Alt+Del - closes all programs) because of crashing CSS, so that might be the solution, I haven't rebooted in two weeks, so did you try reboot or X restart in case of crashed and hidden instance of nautilus (it's running in my computer even thought no folders are open)?


The multiple windows appeared when clicking on my home folder through places ... only.

I tried to reboot many times, and used the close all open windows option as well = failed

Later I did add an icon / launcher for ut2004, but the problem occurred straight away after installing ubuntu.

---

