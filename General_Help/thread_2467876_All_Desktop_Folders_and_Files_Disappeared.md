---
title: "All Desktop Folders and Files Disappeared"
date: 2021-10-10
forum: General Help
---

### Post by dh100 on 2021-10-10
Today I had Ubuntu up for several hours.  I clicked on a file on my desktop and it would not open.  I went to a command prompt and couldn&#8217;t access the Desktop directory.  I rebooted and when I logged in the desktop was empty.  Anyone know what may have happened and if it is possible to recover the files?

 In syslog I don&#8217;t see any corruption errors although I don&#8217;t really know what to search for. (used grep -i corrupt and got nothing so grepped for file and didn&#8217;t find anything obvious.  I did find this
 
 Oct 10 18:02:45 Sol gnome-session[1763]: gnome-session-binary[1763]: WARNING: Could not parse desktop file gsettings-data-convert.desktop or it references a not found TryExec binary
 
 And several several could not parse desktop file errors  Any help would be greatly appreciated.  This is a Ubuntu 18.04.6 system.  Thank you.

 
 
 Dave

---

### Post by dh100 on 2021-10-10
It looks like what happened is that all the folders and files that were in the Desktop directory got moved to snap/Desktop.  
 
 Sorry to have to ask this but why would that have happened?  What should I do?   Just move all the files and folders back to the Desktop directory?

---

### Post by mIk3_08 on 2021-10-11
> **dh100 said:**
> command prompt 
Linux doesn't have any command prompt here we only have terminal here. Linux is not microsoft windows
> **dh100 said:**
> couldn’t access the Desktop directory.
How did you access the desktop directry can you elaborate more on this?
> **dh100 said:**
> In syslog I don’t  see any corruption errors although I don’t really know what to search  for. (used grep -i corrupt and got nothing so grepped for file and  didn’t find anything obvious.  I did find this
 Oct 10 18:02:45 Sol gnome-session[1763]: gnome-session-binary[1763]:
can you paste all the current system logs of your system in Ubuntu paste bin and give us the link here in thread?
> **dh100 said:**
> WARNING: Could not parse desktop file gsettings-data-convert.desktop or  it references a not found TryExec binary

This could be a gnome bug from your system.

---

### Post by The Cog on 2021-10-11
~/snap does not normally contain a Desktop directory, so I am guessing that ~/Desktop somehow got moved. I would just move it back again. This command should do it:
```
mv ~/snap/Desktop ~/
```
Note that ~ is short for your home directory, whatever that is called.

---

### Post by vanadium on 2021-10-12
> **The Cog said:**
> ~/snap does not normally contain a Desktop directory, so I am guessing that ~/Desktop somehow got moved. I would just move it back again. This command should do it:
```
mv ~/snap/Desktop ~/
```
Note that ~ is short for your home directory, whatever that is called.

Here, I would suggest doing this with the graphical file manager. That will preserve the "special" status of the Desktop folder.

If in the mean time, you moved already using the terminal, you can manually edit "~/.config/user-dirs.dirs" and restore the line for the desktop folder to read:
```

XDG_DESKTOP_DIR="$HOME/Desktop"

```

---

