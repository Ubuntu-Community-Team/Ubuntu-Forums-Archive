---
title: "&quot;Clear Usage Data&quot; not working for a date range"
date: 2016-12-22
forum: General Help
---

### Post by one+one+one on 2016-12-22
I use an account shared with other household members so I was looking for a way to clear certain items out of the list of recently used files, and I found **System Settings / Security & Privacy / Files & Applications**.   The configuration options there are pretty nice.  I'm able to exclude anything in a particular folder from appearing in the recent item list, and that is really neat, but it doesn't work retroactively.  So there;s this **Clear Usage Data** button that can be applied to clear out previous history.  But I don't want to clear *all* the history, just the specific items in that one folder I would prefer others not notice so easily.

When I click **Clear Usage Data** I am presented with a list of five choices, to clear history of recently used files and applications from the last hour, last day, last week, specific date range, or all time.  I have attempted to use the third and fourth choices, but the third one is the only one I have successfully used.  In other words, the fourth option, to choose a specific date range over which to clear history, does not seem to work.  It comes up with a default of today's date for starting and ending dates, but if I attempt to change it to anything else, a little calendar of the month appears and gets stuck there, never responding to mouse or keyboard input, and never disappearing until I close every window behind it and then click on the desktop.

This seems like a bug.  Is there a workaround; maybe a way to do this with the command line?  So far the only workaround I have found is to rename the files that I don't want appearing in Recent Files, but that is tedious, and unsatisfactory in the case that I liked the file names they started with.

---

### Post by howefield on 2016-12-23
You could edit the ~/.local/share/recently-used.xbel file and take out entries as required.

Probably better to have everyone using the machine with their own account. <shrug>

---

### Post by fyfe54 on 2016-12-25
I like howefield's suggestion of everyone using the machine with their own account.  

Unless of course, the machine owner/admin actually wants to see what other users have been doing.

---

### Post by one+one+one on 2016-12-25
I could set up other accounts, but didn't want to go through the trouble right now.  I guess it may be less trouble than trying to delete certain items out of the history.  I already looked at ~/.local/share/recently-used.xbel, but there is nothing in the file.  I think the history is all in a sqlite database through zeitgeist.  I don't see any easy solution, short of looking at the source code to see how it works.  I guess I should go ahead and report the bug, and maybe someone will fix it.

---

