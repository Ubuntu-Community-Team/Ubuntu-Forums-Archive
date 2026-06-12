---
title: "'System problem' window keeps popping up"
date: 2014-10-03
forum: General Help
---

### Post by grey1beard on 2014-10-03
A 'system problem' window keeps popping up (see attached screenshot), and this has been happening for the past week or so.
It doesn't seem to be associated with any particular program, and because it then asks for my system password if I click on 'report problem', I hesitate to click on what might be a cunning fishing expedition.
Perhaps paranoia is finally setting in, but I thought best be cautious, and ask here.

---

### Post by grahammechanical on 2014-10-03
I am running the Ubuntu development version of what will be Ubuntu 14.10. So, I often see those kind of crash messages. Usually there is a button labelled Details which will provide information about the crash. The request for your password is also standard because the utility will collect all kinds of log reports which may include passwords. The utility usually connects us to a Ubuntu Launchpad page where we can report a bug. It may even tell us that the bug has already been reported. This is the utility that is detecting crashes.

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

It should be disabled on stable releases such as 12.04 and 14.04. So, it may be the Ubuntu error tracker (woopsie) that you are seeing.

[https://wiki.ubuntu.com/ErrorTracker](https://wiki.ubuntu.com/ErrorTracker)

Regards.

---

### Post by grey1beard on 2014-10-03
Thanks for the reassurance, grahammechanical.
I should have added in the op that I was running 12.04, but I have now followed the request for a password, and sure enough got a window with details available.
lightdm was mentioned, and I clicked on the send error report, but no further action.
If the window does not reappear in the next few re-boots, I'll post the thread as 'solved'.
Many thanks,
John

---

### Post by Habitual on 2014-10-03
next time it pops, open a terminal and run this:
 ```
xprop |grep PID
```

then click on the dialog. Anywhere but a button will do.
Use the pid " = [COLOR=#ff0000]abc[/COLOR][[COLOR=#ff0000]d[/COLOR]]" in an lsof to determine its source

```
lsof -p <[COLOR=#ff0000]PID[/COLOR]> | less
```

Post the results if it seems alarming.

---

### Post by Mike_Walsh on 2014-10-03
> **grey1beard said:**
> A 'system problem' window keeps popping up (see attached screenshot), and this has been happening for the past week or so.
It doesn't seem to be associated with any particular program, and because it then asks for my system password if I click on 'report problem', I hesitate to click on what might be a cunning fishing expedition.
Perhaps paranoia is finally setting in, but I thought best be cautious, and ask here.

Hi.

I don't think it's anything too much to worry about; I regularly get those popping up at the oddest of times.....more so this last 2-3 months (I've been swapping O/Ss around, uninstalling, re-installing.....it's not a big surprise..!

As graham says, what you're seeing is a perfectly normal part of the OS, just doing its job. It is how, as I understand it, Canonical collect information from every individual system running Ubuntu (or its flavours), so as improve the way the OS works, and to simplify the collection of data that helps the devs to fix bugs, etc.

I had it pop up half a dozen times the day I installed 14.04! :p

Regards,

Mike.

---

### Post by Rob Sayer on 2014-10-04
It's true, after you get used to linux you get blase about those sort of error messages.  I've had them and didn't even notice the notice on the panel for at least 5-10 minutes.  I've had my window manager crash and had things running in the background that were unaffected.

I'm one of those people who, when trying out something new like linux, actually wants the system to crash so I can see how well it does it.  Unlike Windoze, linux crashes *beautifully*.

A lot of this is because linux, like unix, was designed as a multi user system used in large installations that can't afford a lot of down time.  For example, in addition to standard input and output there is also a standard error output.

Note this only applies to stable ubuntu releases.  If you install an alpha/beta release like current 14.10, when it crashes ... which it will ... it'll *crash*.

---

### Post by grey1beard on 2014-10-04
Thanks everyone for your various inputs.
Since sending off the bug report, the pop-up has not reappeared, so I am marking the thread as Solved.
Regards all,
John

---

