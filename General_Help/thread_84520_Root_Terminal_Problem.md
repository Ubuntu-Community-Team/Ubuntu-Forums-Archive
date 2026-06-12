---
title: "Root Terminal Problem"
date: 2005-10-31
forum: General Help
---

### Post by H4rm0ny on 2005-10-31
Hi,

I've just upgraded to Breezy which went smoothly. However, I can no longer open a terminal as root. 

Either firing one off from the terminal menu on the taskbar, or opening a new tabbed shell from an existing (non-root) terminal window has the same result: I am prompted for root password. Entering it then results in the window closing without any message.

Everything went fine before. This is one of two extremely annoying bugs that are ruining an otherwise perfect distro.

---

### Post by Pablo_Escobar on 2005-10-31
If You really need to have a root termina create a new launcher.
As a command type in "gksudo gnome-terminal" and voila :)

---

### Post by H4rm0ny on 2005-10-31
That has to be the fastest reply ever!

But I'm on KDE. That's a Hell of a lot of extra packages just to get a root terminal. (And I definitely definitely need one).

---

### Post by Pablo_Escobar on 2005-10-31
For KDE : "gksudo konsole" :)

---

### Post by H4rm0ny on 2005-10-31
Heh! Shaved another minute off your reply time too. 

Many thanks for this. I've tried it and it works. It leaves me puzzled as to why the same konsole fails running off the inbuilt menus, but it's enough for me. 

Just one remaining problem away from the perfect O/S, now.

Cheers,

-H.

---

### Post by radupisano on 2005-11-15
I got one better for ya! I don't know if thisI just found this out myself. 

1.- Go into Add Applications.
2.- Enter your password
3.- Select System Tools
4.- Verify that you have checked "SMEG Menu Editor", if you don't see it, click on "More Programs" and select it. 
5.- Select Apply to install it. 
6.- Go Applications > System Tools > Applications Menu Editor
7.- On the left pane you will see the main menu options for the Applicattions, select System Tools
8.- On the right pane you will see a bunch of apps some checked and some unchecked. The Root Terminal app is unchecked (that is why we don't see it), check it and close the app. 
9.- DONE!!

I just upgraded to Breezy myself and this is the only "defect" worth mentioning about this version of Ubuntu. The more and more I play with this, the more I like this OS....

I know that you got your response a long time ago, but this is another permanent solution... Having this app available will come handy in the future for other "hidden" apps...

Enjoy!

---

