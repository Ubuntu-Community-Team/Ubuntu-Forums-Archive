---
title: "Dropbox not working 14.04 LTS"
date: 2015-09-04
forum: General Help
---

### Post by jhboards on 2015-09-04
I have tried to get dropbox working on 14.04 LTS without success. I have done the following:

1) Installed thru the Ubuntu software center.

2) Uninstalled / reinstalled using Synaptic.

3) Installed using command line in a terminal.

4) Numerous shut downs & restarts.

5) Found dropbox in file manager, clicking link there does nothing.

After the latest restart, I tried (again) to start in a terminal. It appears that dropbox did an install (?). 

I ran the start command again and got the message that dropbox is already running. I cannot find the dropbox GUI open on my PC.

What am I doing wrong or missing here?


[ATTACH=CONFIG]264230[/ATTACH]

---

### Post by DogMatix on 2015-09-04
The Dropbox tray icon is showing right there in the top panel. Can you not access your Dropbox folder from the menu when you click on the icon?

---

### Post by jhboards on 2015-09-04
Candor: I had not noticed that (very small) icon.

If I click the this tiny icon in the top, I get a drop-down menu. I can get a folder to open in Ubuntu that has the dropbox files in it. However; it is behind whatever screen(s) I have open (browse, gedit, etc) and I have to minimize or close out everything down to the desktop to see the folder. 

So, the problem now amounts to being: the only way to get my folder pane to open is to go into search, type "dropbox", then open the folder from the small icon on the top, then navigate under all windows to see the folder pane.

1) How do I get the drop box folder pane to open on top of what I am doing and not buried beneath all the open panes (windows)?

2) I created a desktop icon for drop box. When I click it, nothing appears to happen, but the tiny icon on an open web browser page does appear. I assume that fixing (1) above will fix this too, correct?

Thanks.

---

### Post by DogMatix on 2015-09-04
You should also be able to find your Dropbox folder inside your 'Home' user folder. This can be found in file manager that can be accessed from the 'Files' icon in the Unity launcher on the left of the screen in Ubuntu.

---

### Post by jhboards on 2015-09-04
Yes, it is in my "home" folder.

---

### Post by Geoffrey_Arndt on 2015-09-05
OK jhboards, maybe you need to go to the dropbox website and watch a few of their tutorials on how it works.   It is not like a standard program at all.   It's not supposed to be.   After you install dropbox via the USC or Synaptic, you'll get a system  notification to restart Nautilus (it is tightly integrated with  Nautilus, and a bit less so with other buntu file managers (like Thunar,  Dolphin, etc.).   You should then see the parent dropbox directory.   

The heart of working with dropbox is the "file manager" . . . that's your initial gui so to speak.    You just move files there (and you can create sub-folders).   Immediately that content is auto-uploaded to the dropbox cloud.   Dropbox will then display a pop-up message (in upper right corner of screen) when files have been added, deleted or changed.   (on other PC's that also have Dropbox installed - - this is the sync notification)

The other way to use a "Gui" to manage Dropbox is via the"browser" . . . Firefox or Chrome or whatever you run.    You just register at the Dropbox site, bookmark the site, and the next time you access the Dropbox website, you log in and get to see the folders from your local PC replicated on the website.   The advantage to the website to manage dropbox is there are a few more options there (sharing, permissions for other to edit etc.).   Some of these "extras" depend on your registration AND opting in to the paid version.

Note:  the above may not be 100% in sequence, but it's been so long since my install, I can't recall the exact steps (but as long as you get the dropbox widget, and access their website, you have all the functionality needed.   The program icon in the launcher is not needed (or useful) at all if the service is setup to start upon bootup.

Note2:   Re the windows being hidden under other active windows . . . just use the "show desktop" app (see System Settings>Appearnce tab (enable checkbox).    You should ALWAYS have Nautilus (aka Files open).   Best to have two windows open for real productivity.   Experiment with the "Show Desktop" app to see what it can do for you to manage your windows.  If you want Nautilus to open on top of other windows - - just right click the launcher icon for files, and select the view you want opened.  t will open on top OR just click the launcher icon for files, it will open on top (so no need to search in Dash).   Am assuming you're pretty new to Unity desktop, but it's very manageable without all these extra steps you've been taking (including the unnecessary installs & uninstalls of dropbox . . . I'm surprised it works at all).

---

### Post by jhboards on 2015-09-05
Geoffrey_Arndt: Thanks for taking some time to walk me thru this. Yes, I am new to  the Unity desktop and Ubuntu in general, having "suffered" with windows 7 at work for years. You got me on the right path. Thanks!

---

### Post by Geoffrey_Arndt on 2015-09-05
Very classy response.   You're more than welcome jhboards!   

I'm always glad and proud of those folks that consider "computing" important enough to invest their time in - - to try new "stuff", and to keep learning.

---

