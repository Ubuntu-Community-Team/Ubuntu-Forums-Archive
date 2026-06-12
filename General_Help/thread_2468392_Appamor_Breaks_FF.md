---
title: "Appamor Breaks FF"
date: 2021-10-27
forum: General Help
---

### Post by Quarkrad on 2021-10-27
Specifically web links from thunderbird (78.14.10).  I have no problem with my stand alone machine (and cannot replicate this issue/fault in a vm in my machine) even though both stand alone machines (mine and wife's) are running identical Desktops and versions of software.  Wife's machine is running Mate 20.04 ( up to date) with firefox 93.00 and Apparmor 2.13.37 - everything has been installed via Synaptic (on both my machine/vm and wife's machine).  What happens on her machine is .... if you click on a web link in an email firefox launches with a window including her normal bookmarks in the bookmarks toolbar (i.e. it looks like her unique version of firefox).  However, ff is totally unresponsive, you cannot enter a url, you cannot type things like about:config in the address bar and there is no drop down menu if you click on *file, edit, help* etc.  Totally dead.  I have looked in /.mozzilla and no new profile is created - just her normal profile is present.  However, **if **ff is running in the background when you click on a web link in tb then ff launches displaying the web page (as it should do).  This sequence of events happens only when apparmor is installed.  If I uninstall apparmor and restart then clicking on a web link in an email launches ff normally to the web page.  I have disabled apparmor via sudo systemctl disable apparmor but this 'fault' is still present.  It doesn't matter whether appamor is installed on its own or with all the profiles - the only way for this machine to operate normally is for apparmor to be uninstalled.  As far as I can tell both machines are identical but there is obviously a difference somewhere.  (I have reinstalled the software on her machine so I need some help as I'm not sure what to do next).   As a temporary measure I have uninstalled apparmor on her machine but would rather have it installed for the extra security it offers/

---

