---
title: "Enabling bootup text"
date: 2008-03-24
forum: General Help
---

### Post by revenant138 on 2008-03-24
My screen goes blank while the kernel boots up, after bios. It comes back on at the graphical login. Is there a way to set it up so i can see the bootup text scrolling by? Or get a graphic in there? the blank screen for 10 seconds is annoying

THX :D

---

### Post by y-lee on 2008-03-24
See [ No loading screen]("http://ubuntuforums.org/showthread.php?t=699492"). Hope that helps :)

---

### Post by raja on 2008-03-24
Make a copy of menu.lst and then open it for editing.
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp
sudo gedit /boot/grub/menu.lst
```

Now in the 'kernel' line, just delete the 'quiet' option. Reboot and you should be done!

---

### Post by revenant138 on 2008-03-27
Thank you all, I've enabled boot text just fine. Now, however, i'd like to get usplash running and I cant seem to do it. I've been working on it for a bit now, and here's what I've tried. I'm trying to get the kubuntu theme working.

1 - changing the /etc/usplash.conf resolutions
2 - reinstalling usplash, and the kubuntu-artwork-usplash packages
3 - running the update-usplash-theme usplash-theme-kubuntu thing
4 - installing startupmanager, no help.
5 - between all these running 'sudo usplash' to see if i'd gotten anywhere

I cant seem to find any howtos telling me anything more than these. Any ideas? :confused:

---

