---
title: "Shell scripts in Terminal from Panel and at Startup (16.04)"
date: 2016-10-22
forum: General Help
---

### Post by col48 on 2016-10-22
I have two short scripts which are behaving differently despite having (as far as I can see) identical contexts.  I do want to use them differently, but can't see ways forward in either case.

**1. Script A**. This tells me how much traffic there is between computer and router - the best I can do for bandwidth usage.
Here are the contents of my webmonitor.sh file

```
vnstat -d ;sleep 2
vnstat -m ;sleep 30

```

This file was inherited from 12.04, where it runs from a panel icon (as an Application in Terminal, with just the full path to the filename as the command) with no problem.  A Terminal appears and the output is displayed conveniently for me to examine.
When I click on the 16.04 panel  icon with identical properties, the icon flashes for a moment, but as far as I can see no Terminal appears.
If I click on the file itself and choose Run in Terminal, it does what I expect.
**What can I do to run it from the panel?**
[B]
2. Script B[/B].  This changes the screen resolution - the native one for the monitor is in fact slightly too big. 
This is the screenres.sh file

```
xrandr -s 1600x1000
```

This was unnecessary in 12.04, but changing Applications>System Tools>Screen Display does not stick across a reboot in my 16.04. The reason is undiagnosed.
So I have a panel icon, which works fine, set up just like script A.  Side issue: why does this work and the other not?
I would like to have it run on startup, but just using the file name (as in the panel) as the command to run has no effect.
**How can I achieve this?**

It just may be relevant that I am using Gnome Classic Metacity.

---

### Post by CantankRus on 2016-10-22
Try re-adding your script to the panel.
Make sure webmonitor.sh is executable and then drag and drop it to the panel
and the properties box should open where you can set it to open in terminal.

If it doesn't work post the full content of your webmonitor.sh  file.

For running at startup, again make sure any script is executable and add the full path as the command.
Right clicking on the script from the file browser will allow you to copy and paste in the correct path in the command box.
Don't use  "~" as an abbreviation for your home directory in the path.
The screenres.sh script may need a **sleep** command when run at startup.

---

### Post by col48 on 2016-10-23
(This is about what I called **Script A** - for which the question is solved)

Well, well!

> Make sure webmonitor.sh is executable and then drag and drop it to the panel
and the properties box should open where you can set it to open in terminal.


This worked!
The script was already executable (permissions rwxrwxrwx).
Drag (from the file manager) & drop onto the panel, set properties to launch within a Terminal, give it a Name, put in a comment about it and change the icon.  And it still works!

Looking at Properties there is no way to distinguish the two Panel objects.  (The previous one was made by adding an empty panel object and changing properties to suit, including typing in the script file name - correctly!)

Any idea - for the record - why the old one does not work, when Script B, which was set up in exactly the same way, worked from the start?

Again, for anyone looking at this thread in the future, both scripts were listed in full in my original post.

---

### Post by CantankRus on 2016-10-23
When you drop a script on the panel it creates a .desktop file @ **~/.config/gnome-panel/launchers**
Compare the different .desktop files by dragging them off the panel into an open gedit window. 
[ATTACH=CONFIG]271744[/ATTACH]
If permissions are ok the only thing I could see being wrong is incorrect path to script.

> **col48 said:**
> 
Again, for anyone looking at this thread in the future, both scripts were listed in full in my original post.
When posting a script you should include the first line shebang (eg #!/bin/bash) as an error here can sometimes be the cause.

With your xrandr startup, you can just add the xrandr command directly to startup applications. 
You will then find the created desktop launcher in  **~/.config/autostart** which
you can edit to delay the running, if needed, by adding this line to the file...
```
X-GNOME-Autostart-Delay=5
```
[ATTACH=CONFIG]271746[/ATTACH]

---

### Post by col48 on 2016-10-23
I didn't know you could do that for a panel item.

What it showed up was indeed a small but unforgiving error in the path for the unworking item; when this was corrected it also worked.  (Oops, on my part - I ought to have noticed.  Sorry!)
There is no shebang line in the scripts:

[ATTACH]271755[/ATTACH]

Thanks, CantankRus for your patience.

---

