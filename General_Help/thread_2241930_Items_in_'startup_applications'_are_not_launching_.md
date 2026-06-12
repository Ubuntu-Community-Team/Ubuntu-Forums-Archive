---
title: "Items in 'startup applications' are not launching at boot"
date: 2014-08-29
forum: General Help
---

### Post by snurfle on 2014-08-29
Ubuntu 14.04
Lenovo W530

I originally assumed this to be an issue with xscreensaver - 'xscreensaver daemon doesn't seen to be running...'
Every posting I could find said "add it to 'startup applications'".
I have done that, but it never loads it or generates any error messages or log entries that I can find.

The other day, I ran dispcalgui to create an icc profile for the laptop, and one for each of the conference room screens in the office.
The profiles were created with no issues, but the profile loader does not launch at startup, even though it has an entry in the 'startup applications preferences'

while searching for an answer to this, I found a suggestion to add a startup item with the command:  date > /tmp/startuptest.txt
This command works if i run it in a terminal window, but does nothing when added to the startup applications.

The final test I ran was this morning; I installed dropbox.
The launcher was added to startup applications, but it does not actually launch until I manually fire it off from the launcher.

The only conclusion I can reach is that ubuntu is completely ignoring the items in 'startup applications'.

There are no apparent errors located in any of the logs that I am aware of.

This is a month-old installation, with all of the current updates installed.

Is there some way of checking the results of the items in startup applications?  I'd like to see if they are even attempting to run!

---

### Post by Dennis N on 2014-08-29
> Is there some way of checking the results of the items in startup applications? I'd like to see if they are even attempting to run!

To see what processes or applications are running, install **htop**. It runs in the terminal and has a search function.

For example:
To see if xscreensaver is running, press F3 (to search) and type 'xscreensaver' in the search box. It will match your entry as you type it. Press F3 again for next match. If there is no match, the typed text turns red.

You can scroll left and right with the arrow keys (mouse doesn't work here) to see the entire line in the display (or use full screen).

---

### Post by ian-weisser on 2014-08-29
Hmmm. Perhaps some earlier startup application is crashing, preventing run-parts from starting later applications.
Do *any* startup applications start?

Are there any error messages in /var/log/syslog?

---

