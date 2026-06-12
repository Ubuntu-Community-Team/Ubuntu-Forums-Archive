---
title: "GNOME laggy/freezing UI"
date: 2015-02-28
forum: General Help
---

### Post by cuzza40 on 2015-02-28
Hello everyone!

It's my first post, so please forgive me if this is the wrong place, but I've been trying various things for the past several days and I'm hoping someone will know, if not a solution, at least have an idea of how to even search for this... I'm completely stumped as to how to even properly describe the problem to search for it, and I can't believe I'm the ONLY one to have seen this issue...

I have Ubuntu 14.10 installed on a Chromebook c710, and I've just recently done an update of updated packages for the first time in several months (I never connect it to the internet, as it's mostly used for displaying Impress presentations in classes), which has caused a huge problem.

I'll take a crack at describing the problem, but I'm also attaching a link to a youtube video of the issue, since I'm sure my description will be inaccurate.

When something happens in the UI, such as opening a window, or a menu, the screen starts to show the action, but then the UI doesn't update as I do things.  For example, if I have a folder highlighted in an open file manager, and I move the arrow keys, the highlighted file DOES move around correctly, but the UI just doesn't display it until I do something to force it to redraw, like move the window.  It does this for practically every application, and I'm at my wit's end.

Here is the youtube video, along with timecodes and explanations of what I'm seeing:

[https://www.youtube.com/watch?v=TOFZBPXGyWM](https://www.youtube.com/watch?v=TOFZBPXGyWM)

0:13 - I click the Applications menu.  Notice that the menu opens, but stops partway through forming, and is now semi-transparent.  The menu IS open and responding, but the screen is simply not refreshing anything but the cursor position.  Note that I CAN open an application.
0:33 - I open Handbrake despite the menu not updating its display at all.
0:51 - I open the places menu, and the same UI lag results.
0:55 - I open the file manager.  The same UI lag.
0:58 - Despite pushing the down arrow repeatedly, the highlighted file position is not updated in the UI until I physical drag the window around to force a redraw.

If anyone has encountered anything like this before, or if there's any further information I can give, or anything, I'd be extremely thankful.  I'm literally begging for any insight anyone might have...

---

### Post by Bucky Ball on 2015-02-28
Welcome. Perhaps open a terminal and update there for a closer look. Issue these four commands one at a time, hitting enter after each and letting it do its thing. You will need to enter your password after the first command. It won't be visible when you type, but that's as it should be:
```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

Report any and all errors/suspicious looking messages.

If the screen makes it impossible to issue these commands due to lag or another problem, hit control+alt+F1, login and update there. You can then restart with:

```
sudo reboot -h now
```

---

### Post by cuzza40 on 2015-02-28
Many thanks!

I actually had an epiphany about an hour ago and tried flashing the newest coreboot bios onto the unit, and that seems to have solved everything.  Thanks for the help!

---

### Post by Bucky Ball on 2015-02-28
Good news. Well done. ;)

---

