---
title: "Start-up Apps in XUbuntu"
date: 2007-03-01
forum: General Help
---

### Post by eSystm on 2007-03-01
Get ready, I'm the long winded type...

**Background:**

I am a network admin for a Non-Profit Organization. We have a hefty SBS 2003, Exchange, SQL and Terminal Server set up, but our end user systems are lacking. This is mostly for the fact that the users do all of their work by remote desktop to the terminal server... These low end computers that my users are forced to use are running Windows 98 (AHHH!!!) because nothing else Microsoft can run on them except remote desktop. I'm tired of them complaining about Windows 98 (because I don't have the funding from the higher ups to get ALL new computers). It's not supported by Microsoft anymore, there are no more updates or virus protection and it can't open image files very well. SO this is what I have decided to do:

Step 1: Boot from a XUbuntu CD
Step 2: Wipe hard drive of all things Microsoft and install XUbuntu
Step 3: Install Terminal Server Client
Step 4: Make one Admin account
Step 5: Make one Basic User account that auto logs in at start up
Step 6: Un-install apps that the users won't need and configure some misc settings

End Product: A operating system that is fast on old machines that can look at images, video, surf the web faster/easier, is more secure than some Windows 98 hack job making everyone happy and more productive....and the best part, it was FREE.

**Question:**

How do I get the Terminal Server Client (and other applications) to automatically start up when the Basic User account logs in to the GUI? For some reason some people here have a difficult time finding it in the Applications menu because it doesn't look like Windows.

Thanks, looking forward to more Ubuntu Linux.

- e

---

### Post by kerry_s on 2007-03-01
menu> settings> autostarted applications

Just click on add, put a name, and the command for the application.
example:
 I start conky with just
 conky<- starts conky
but
You can also just point to executables or put the command that works in terminal.
/home/user/.login <- points to my script to play login music
xset s off off<- turns my screensaver off
xset dpms 0 0 300<- makes my computer screen turn off after 5min of no activity.

---

