---
title: "logout/restart/shutdown choices missing"
date: 2017-02-11
forum: General Help
---

### Post by r.stiltskin on 2017-02-11
I just upgraded this laptop to xubuntu 16.04 a couple of days ago.  Yesterday there was a Log Out button on the main menu offering choices of Log Out, Restart, Shut Down.  Suddenly it seems I have only "Log Out" buttons (one on the main menu on the top panel, another in the desktop Applications Menu), and only after logging out there is a button on the top panel offering restart and shut down options.  Why are these options no longer available before logging out?

---

### Post by Keith_Helms on 2017-02-11
Right-click on the top bar and then select panel and panel preferences from the popup menu.  Select the items tab on the window that appears.  Do you have an item named action buttons?  If you do, highlight it and click the little gear icon on the right to edit it.  Check off the actions that you want to be visible.  If you don't, click on the plus icon to add a new item and select action buttons and configure it to display the actions you want.  You can use the up and down arrow icons to arrange the items on the top bar in whatever order you like.

---

### Post by ajgreeny on 2017-02-11
The whisker menu on my Xubuntu 16.04 as well as the Main menu which I added to check this both have a Logout button which takes you to a choices dialogue, but not separate button for shutdown, Reboot, Suspend, etc, and I don't remember them being in 14.04 either.

All of those options are, however, available in the Action Buttons applet mentioned by Keith, which is what I use.

I have also made keyboard shortcuts for instant shutdown and instant suspend on my desktop machine; both very useful when in a hurry.
I use the Pause/Break key with command **xfce4-session-logout --halt** for shutdown,
and Pause/Break+WinKey with command **xfce4-session-logout --suspend** for suspend.

---

### Post by r.stiltskin on 2017-02-11
@Keith: Thanks, I added an action button to the panel and that works, but ...

> **ajgreeny said:**
> The whisker menu on my Xubuntu 16.04 as well as the Main menu which I added to check this both have a Logout button which takes you to a choices dialogue

that's what I was talking about.  Sorry I didn't explain myself clearly.  Three days ago I was investigating a 90-second delay during the shutdown sequence and rebooted probably 20 or more times.  I'm sure that I was using the logout button on the main menu, which when clicked brought up a choices dialogue offering logout/restart/shutdown.  But now, my main menu logout button just immediately logs out -- no dialogue.  I'm not aware of having done anything to change that and I'd like to restore it if possible.

---

### Post by Keith_Helms on 2017-02-11
Hmmm.   On my Xubuntu 16.04 system both the logout button in the action button and on the main menu bring up the logout/restart/shutdown choice you mention.  I haven't found anywhere you can configure that and don't know why it now works differently on your system.

---

### Post by Keith_Helms on 2017-02-11
The logout button invokes a command called xfce4-session-logout.  If you run that from the command line and supply the option --logout then it immediately logs you out without presenting a window with the logout/restart/shutdown options.   So the question is, do you have that --logout option set somewhere.

---

### Post by Keith_Helms on 2017-02-11
Aha.  Think I found it.  Go into settings manager and select the session and startup icon in the system section.  Make sure Prompt on logout is checked.

---

### Post by r.stiltskin on 2017-02-11
Adding to the mystery, I tried logging in as another user and for that user the logout buttons on the Whisker Menu (left corner of the top panel) and on the Application Menu (right-click on desktop) BOTH bring up a dialogue offering Log Out/Restart/Shut Down/Suspend options.  But for my primary user account, the buttons immediately log me out.  (So apparently something that I installed or uninstalled in the past 2 days has changed the behavior for my primary user.)

In the menu editors, in both user accounts the command associated with Log Out is "xfce4-session-logout" which seems to be a shared library in /usr/bin so presumably should not vary by user unless there's a configuration file that it accesses someplace.

By the way, I just noticed the same screwed-up behavior on my desktop machine which is still running 14.04 -- I just never noticed because on that one I rarely change users and almost never shut down (and I use a panel action button when I do).

---

### Post by Keith_Helms on 2017-02-11
You were probably typing when I posted my last response, so look at post #7 and see if that solves your problem.

---

### Post by r.stiltskin on 2017-02-11
> **Keith_Helms said:**
> Aha.  Think I found it.  Go into settings manager and select the session and startup icon in the system section.  Make sure Prompt on logout is checked.

That's it!  As I said I just recently upgraded so I've been tweaking things.  Must have inadvertently unchecked that when I set it to save session on logout.

Many thanks.

---

### Post by ajgreeny on 2017-02-11
Great news! Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by markackerman8@gmail.com on 2017-03-10
Great troubleshooting - awesome

---

