---
title: "multiple commands help- Xubuntu 12.04"
date: 2014-09-19
forum: General Help
---

### Post by cris7 on 2014-09-19
I'm trying to create a launcher that will (directly or indirectly) open up a few windows for me that remain up until I manually close them.  However, the gedit and custom Terminal session keep dissapearing on me.  The setup I made worked fine on Fed8 and u10, but not on Xubuntu 12.04.

For u10 I had to change the launcher into a script, and add a launcher that pointed to the script (at least it was the only thing I could get to work).

In the end, I need to click a launcher on the desktop, and get the following results (i've inserted the commands I'm currently trying to do this with):[INDENT=2]1- Copy a file to another location (it is wiped out automatically at the destination, I have to have a saved copy elsewhere to avoid repeating work)
[/INDENT]

[LIST]
[*][INDENT=2]scp /home/some/text/file /a/programs/directory/file
[/INDENT]
 
[/LIST]
[INDENT=2]
2- Open this newly moved file in a gedit window, without a tailing terminal hanging on the screen
[/INDENT]

[LIST]
[*][INDENT=2]nohup gedit /a/programs/directory/file
[/INDENT]
 
[/LIST]
[INDENT=2]
3- Open up firefox, must be a new window, at a specific website
[/INDENT]

[LIST]
[*][INDENT=2]firefox -new-window http://example.com/[/INDENT]
 
[/LIST]
[INDENT=2]
4- Open up a custom terminal session in a separate window
[/INDENT]

[LIST]
[*][INDENT=2]/some/directory/launchCustomTerminal[/INDENT]
 
[/LIST]

So the Script that my launcher refers to looks like this:[INDENT=2]#!/bin/bash
scp /home/some/text/file /a/programs/directory/file
nohup gedit /a/programs/directory/file &
firefox -new-window http://example.com/ &
/some/directory/launchCustomTerminal
[/INDENT]

I don't have a personal need to have this set up as a launcher that refers to a script that runs everything.  If it can all be done straight from the launcher then that's fine as well.

Any help would be appreciated.

Thanks,

---

### Post by cris7 on 2014-09-22
Any help would be appreciated, thanks!

---

### Post by sudodus on 2014-09-22
Welcome to the Ubuntu Forums :-)

This works for me (started from a terminal window)

```

#!/bin/bash

scp /home/some/text/file /a/programs/directory/file
gedit /a/programs/directory/file &
firefox -new-window [http://example.com/](http://example.com/)
/some/directory/launchCustomTerminal &

```

I don't know if that is OK, or if you want some automatic starting. If you use it as a cron job, there might be problems:

1. The environment is very simple, so you need explicit paths

2. There might be problems with the graphical display, that the cron job is not booted from your desktop session

3. Instead you can make it an 'autostart' job. You find the tool for it via the menu or this command

```
xfce4-session-settings
```

1. I'm not sure if you need superuser privileges to add your script, in that case

```
gksudo xfce4-session-settings
```

2. I'm not sure if the script will run as it is, or if it should be launched via a graphical program, for example xterm

```
your-script
```

or ```
xterm -e your-script
```

In any case you should make the script executable.

```
chmod ugo+x your-script
```

I suggest that you test these alternatives until you find something that works.

---

### Post by cris7 on 2014-09-22
Thanks [**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021"), I'll check all that out and play with it and post back here for others to reference.  

The custom terminal command I use opens 4 tabs, each with it's own preset environment.  No need for su privelages, and I don't want to mess with the cron jobs for this.

Thanks again!

---

### Post by cris7 on 2014-10-16
I got it worked out, finally!  Turns out there is a bug in Gedit related to language highlighting settings in the metadata for the file.  I should have tried this line by line in a terminal window first to identify the issue, because I would have seen an error message ending with this (I can't reproduce now to get the full error again):

*:update_syntax: assertion failed: (state->context != NULL)*


Found the fix here...

[http://superuser.com/questions/526722/why-cant-i-open-a-certain-file-in-gedit](http://superuser.com/questions/526722/why-cant-i-open-a-certain-file-in-gedit)


Here's how my script looks now (change the **bold** sections to match what you need)...


#!/bin/bash
scp **/home/some/text/file /a/programs/directory/file**
#if errors or gedit crashes, uncomment the following line and rerun the script
#gvfs-set-attribute **/a/programs/directory/file** metadata::gedit-language ''
nohup gedit **/a/programs/directory/file** &
firefox -new-window **[http://example.com/](http://example.com/)** &
** /some/directory/launchCustomTerminal**


I thought this meant that I couldn't have a highlighting mode on, but after running the fix on the original file (in the 4th line of the updated script above, without the # at the beginning), I was able to correct the highlighting mode.  Since that works, I've commented out this line so it's not active (again, line 4 above), but left it there in case this comes up again.

Hope this is helpful for somebody!

Thanks again [**[COLOR=#C61919][B]sudodus**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1499021")  for your help!

---

### Post by jamesisin on 2014-10-16
Since you have solved your issue you should mark this thread as solved.

---

### Post by sudodus on 2014-10-17
> **jamesisin said:**
> Since you have solved your issue you should mark this thread as solved.

+1

Congratulations and thanks for sharing your solution, *cris7* :KS

Finally, please click on **Thread Tools** at the top of the page to mark this thread as SOLVED

---

### Post by cris7 on 2014-10-17
Thanks for the instruction on the Thread Tools.

---

