---
title: "[SOLVED] Ubuntu White Screens after installing restricted drivers"
date: 2008-06-15
forum: General Help
---

### Post by Jordanwb on 2008-06-15
I'm installing Ubuntu onto a friend's computer for him since he doesn't like Vista, he has a ATI video card (Radeon x1600, same as mine). I ran all the updates. I activated the restricted modules, rebooted. After logging in the screen goes white. I didn't have this problem with my computer and I'm using the same CD. After doing a search it appears I'm not the only one with this problem:

[https://bugs.launchpad.net/ubuntu/+bug/195055](https://bugs.launchpad.net/ubuntu/+bug/195055)
[http://ubuntuforums.org/showthread.php?t=714034](http://ubuntuforums.org/showthread.php?t=714034)

In the launchpad link, one guy said reinstalling worked. I did that and I still get the problem.

I tried the suggestions in the thread on this forum and it didn't work.

When I press Ctrl+Alt+Backspace I see the Hardy Heron background for a split second.

---

### Post by PmDematagoda on 2008-06-15
Perhaps it could be Compiz causing the problem, after you login and reach the white screen, try killing it by switching to a tty by pressing Ctrl+Alt+F1, execute:-
```
killall compiz.real
```
and moving back to the normal tty by pressing Ctrl+Alt+F7.

---

### Post by Jordanwb on 2008-06-15
Yay I can get to the desktop. I'll reboot and see what happens.

White screened again. Perhaps I'm to uninstall compiz?

---

### Post by ProbablyX on 2008-06-15
If not, did you generate a new xorg.conf?

I had this issues in Fedora (year+ ago) the error was that there was some line in /etc/X11/xorg.conf (the settings file for the graphical interface) that made everything go bad.

I use an nvidia card now, but look for the settings program for ATI cards.
First
```

# sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bup.20080615

```

This will move your xorg.conf and make a back up file with todays date in it so you can go look for it later knowing when you made it.

After this try and generate a new xorg.conf with ATI's tool. Even if you ran it before it might not have created a new file, just edited the one you have.

---

### Post by PmDematagoda on 2008-06-15
If you don't want to use Compiz, just remove the entry in Sessions in System>Preferences>Sessions, that should do it.

---

### Post by Jordanwb on 2008-06-15
> **ProbablyX said:**
> If not, did you generate a new xorg.conf?

I had this issues in Fedora (year+ ago) the error was that there was some line in /etc/X11/xorg.conf (the settings file for the graphical interface) that made everything go bad.

I use an nvidia card now, but look for the settings program for ATI cards.
First
```

# sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bup.20080615

```

This will move your xorg.conf and make a back up file with todays date in it so you can go look for it later knowing when you made it.

After this try and generate a new xorg.conf with ATI's tool. Even if you ran it before it might not have created a new file, just edited the one you have.

I sortof did. When I got to grub I selected Recovery Mode and deleted the xorg.conf file. But I never got any menu to configure Xorg. Where do I get this ATI tool you speak of?

> **PmDematagoda said:**
> If you don't want to use Compiz, just remove the entry in Sessions in System>Preferences>Sessions, that should do it.

I don't see Compiz in the list.

There's something else weird that's going on. I started Synaptic and I can't see the title bar and when I clicked on Search, the search box was at the very top-left. Plus neither Synpatic or firefox show in the bar at the very bottom.

But still why did the install of the restricted driver go perfectly for me, but for his comp it's all messed up? I used the same CD, and we both have all the updates, :confused:

I'll try reinstalling, enabling the drivers, then update and see what happens.

---

### Post by PmDematagoda on 2008-06-15
Do you both have the same VGA cards?

---

### Post by Jordanwb on 2008-06-15
Yes. Both X1600 AGP. I reinstalled and it still white screens.

---

### Post by PmDematagoda on 2008-06-15
Well, unfortunately I can't help you out much since I am not really an ATi expert, sorry. But perhaps you may want to try using the ati driver, though this means that there will be no compositing or effects.

---

### Post by Jordanwb on 2008-06-15
Thanks anyways. But still it's weird. On one computer it works, but another it doesn't.

---

### Post by Jordanwb on 2008-06-17
I did a complete format of the entire drive and it still whitescreens. I'll try using version 7.10 and see what happens.

---

### Post by Kronie on 2008-06-17
WAAAIT! i have the cure for it! i had same problem! 
[http://ubuntuforums.org/showthread.php?t=481138](http://ubuntuforums.org/showthread.php?t=481138)

i had the same thing.. i got it after installing drivers from ati website over ati accelerated 3d driver..
then screen was white after login.. you can also start gnome failsafe session to go around the problem, but u will have no effects/awn deck or such stuff...

---

### Post by Jordanwb on 2008-06-18
Ok Kronie I'll give that a try. I was wondering if the updates being downloaded during OS install messed it up or something? It's happened before: updates were messing with grub installation on my laptop.

[Edit] What the heck? I installed the drivers as per your instructions, restarted and it works now. :confused: I should add this to my "top ten computer annoyances" list: Software that works one minute and not the next for no reason.

---

### Post by Kronie on 2008-06-18
great :P

---

