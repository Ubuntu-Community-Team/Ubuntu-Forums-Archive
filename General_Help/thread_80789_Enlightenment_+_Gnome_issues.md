---
title: "Enlightenment + Gnome issues"
date: 2005-10-23
forum: General Help
---

### Post by joflow on 2005-10-23
Hi,

I have enlightenment (e17) and gnome (almost) working together thanks to the 5.04 guide.

I just have a couple problems. 

1.  Firefox isn't working correctly.  There are no minimize, maximize, and close buttons on the far right side. 

2.  I have no earthly idea of how to install new themes for e17.  I've downloaded the milky theme but I don't know how to get it to show up under the themes panel.

I really like e17, its great.  I just wish I could get these few issues sorted.

Thanks.

---

### Post by joflow on 2005-10-23
found out what the firefox problem is.  The buttoms are there, they're just covered up by the top gnome-panel.  Quite annoying.  Anyway to make maximized windows stay below the gnome panel like metacity?


I'm really eager to get this set up working.  I'm an eye candy freak and e17 is unlike anything I've ever seen on any platform (just found out it supports animated backgrounds!! eager to get that working as well).  This has the potential to make me switch from xp to linux as my primary OS.  I just don't like the default theme and I need the little quarks sorted.

---

### Post by bvc on 2005-10-23
Just put the e17 theme/s in .e/e/themes

backgrounds go in .e/e/backgrounds

In case you don't know, I did these gtk themes to go with e17.
[http://gnome-look.org/content/show.php?content=28051](http://gnome-look.org/content/show.php?content=28051)
[http://gnome-look.org/content/show.php?content=28489](http://gnome-look.org/content/show.php?content=28489)

Check out the User Guide here
[http://get-e.org/Main/News/index.html](http://get-e.org/Main/News/index.html)

---

### Post by joflow on 2005-10-23
Thanks...got milky up and running and its SWEET.

Got some animated backgrounds too.  Now if I could just fix this maximized window issue.

---

### Post by bvc on 2005-10-23
Doubt that'll ever happen. E17 is not made to run with the gnome-panel, but w/o a panel (notification). Middle-click is it's 'window list' and I love it that way. Oh, I haven't tried but have you rt-clicked the titlebar and tried setting the widow states? It probably only applies to E17 wm windows but it's worth a try.

---

### Post by joflow on 2005-10-25
Really sorry to hear that, its driving me nuts.  I love the gnome + enlightenment combination through.

---

### Post by chien on 2005-11-02
ok, ive been using an enlightened gnome (e17)  for about a week now, here are the problems that I found:

- NO TASKBAR!!!!! (This is very annoying), i miss the glowing of the incoming messages from gaim.

- Maximizing the windows goes all over the top of the gnome-panel ( I have my gnome-panel at the top). Everytime that I mistakenly maximize a window, i have to move the gnome-panel, so that i can access the minimize button of the window. VERY ANNOYING TOO!

- The gnome Desktop blocks the enlightenment one, i have to go to desktop number 2 in order to customize enlightenment.

- The system tray sometimes doesn't work.

- Everytime that I logging, i have to wait for like 5 mins.

- Lack of themes.

- Enlightenment's forum is dead.

---

### Post by Dr. Nick on 2005-11-06
This is from shadoi on another thread to fix the mxamize problem 
Use this command to enable the smart maximize policy (this will likely be the default when e17 is released.):
enlightenment_remote -maximize-policy-set SMART

I am trying to get some other bugs worked out myself, I think I can help with the desktop issues ,you say you have to switch desktops to configure e17 because the  computer,home etc icons and the standard right click are in the  way?
If so open applications-system tools-configuration editor/ go to apps-nautilus-prefrences and uncheck show desktop. this will take all the icons off and should work.

I am also suffering from the taskbar not working well and the system tray , but if you just load the modues from enlightnment and remove gnomes then it is usable.

---

