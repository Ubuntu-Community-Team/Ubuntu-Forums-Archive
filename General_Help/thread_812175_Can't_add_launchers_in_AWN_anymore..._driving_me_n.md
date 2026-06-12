---
title: "Can't add launchers in AWN anymore... driving me nuts!!"
date: 2008-05-29
forum: General Help
---

### Post by Spoonboy on 2008-05-29
Just as the title says, for some reason I can't add any launchers to AWN. I used to so I don't know what's changed.

basically if i try and drag an existing desktop launcher icon onto the panel it just moves back when I try and drop it on the bar.  The exact same thing happens when I do the same thing in the AWN manager launchers bit.

I've tried uninstalling the whole thing (both the bzr version and the standard one in the repos) and deleting the /config/awn dir in my home directory and reinstalling to no avail - it seems to remember my last settings as it has the same launchers icons.

I think there's a settings folder somewhere I need to delete then reinstall. Problem is I can't find it!

Any help much appreciated.

---

### Post by pmaconi on 2008-05-29
Have you tried to create a launcher through the AWN preferences manager? That should still work for you.

---

### Post by Spoonboy on 2008-05-29
I think I can but that's just a pure hassle typing in all that crap just to get what is effectively a shortcut.

However in the launcher options in AWN manager I used to be able to drag icons onto the list of launchers and the would be added to the panel. Now whenever I try and drag an icon onto it, it just drags itself back as soon as I let go of the LMB.

I'm new to linux, drag and drop is preferable to typing in stuff!li

---

### Post by pmaconi on 2008-05-29
Read the last post of [this thread]("http://ubuntuforums.org/showthread.php?t=718062&highlight=awn+drag+shortcut"). I think this may answer your question.

---

### Post by Spoonboy on 2008-05-29
unfortunately it doesn't. I can't drag any icons from anywhere

it used to work flawlessly, I wish I knew how to remove it completely. I'm new to ubtunu/linux and have reinstalled hardy 5 times in the last few weeks due to various niggles. Even a user friendly distro like ubuntu can be a pain the A.

---

### Post by pmaconi on 2008-05-29
Then I'm not sure. But I would suggest trying the manual way to make a launcher through preferences (you only need to type a name and description. Clicking the 'open' button lets you browse for the file).

---

### Post by Spoonboy on 2008-05-30
I actually just tried to create a launcher manually, and whilst it lets me make one, it doesnt appear on the panel.

---

### Post by rune0077 on 2008-05-30
Try adding the launcher (just drag and drop it) to ~/.config/awn/launchers

I'm not sure if that folder is even used anymore, since mines empty, but that's how I originally added my launchers.

---

### Post by pmaconi on 2008-05-30
Also make sure that you have the Launcher/Taskmanager applet enabled.

---

