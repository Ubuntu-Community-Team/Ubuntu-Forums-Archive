---
title: "configure extra mouse buttons"
date: 2013-11-26
forum: General Help
---

### Post by samsamsam2 on 2013-11-26
I am trying to configure the two side buttons on my mouse to page up and page down. 
According to [https://help.ubuntu.com/community/ManyButtonsMouseHowto](https://help.ubuntu.com/community/ManyButtonsMouseHowto)

 "If you have installed the GNOME environment (default for Ubuntu) you *already* have the software needed to get the "6th" and "7th" mouse buttons working (forward/backward on most mice)! "

2 questions:

1) Which software are they talking about ? Compiz doesn't have any options to setup the mouse buttons.
2) **xinput test <my_mouse_id>** shows that those two button numbers are buttons 8 and 9. Do I have to use imwheel?

thanks
):P

---

### Post by ajgreeny on 2013-11-26
Here's a copy of the .xbindkeysrc file tyhat I used to need for "page backwards" and "page forwards" in my web-browsers and file managers, but which is no longer needed as the system does this without the need now (in 12.04).

You may be able to glean all the info you need from the comment lines in the file (they start with #) which are there as a reminder to me how I did it.

```
# Entries to enable forward & backwards navigation in nautilus with mouse buttons.

#sudo apt-get install xvkbd xbindkeys x11-utils.
#Ubuntu versions before 9.04 (Jaunty Jackalope), the x11-utils package needs to be swapped for xev.

#Terminal command:-
#xev | grep ', button'         Press mouse buttons and note output, eg

#state 0x10, button 8, same_screen YES
#state 0x10, button 8, same_screen YES
#state 0x10, button 9, same_screen YES
#state 0x10, button 9, same_screen YES

#Back in terminal, we need to create a new file to configuration xbindkeys.

#gedit ~/.xbindkeysrc

#This will load up Gedit to add content to the new file. This file needs to contain the following:

#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
#  m:0x0 + b:8
#"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
#  m:0x0 + b:9

#Notice the &#8220;b:8&#8243; and &#8220;b:9&#8243; portions of the text. This is where I configure my mouse buttons. So, if your mouse buttons are 6 and 7, then you need to change &#8220;b:8&#8243; and &#8220;b:9&#8243; to &#8220;b:6&#8243; and &#8220;b:7&#8243;, respectively.

#Set xbindkeys to autostart at session start in System->Preferences->Startup Applications.

"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Left]""
  m:0x0 + b:8
"/usr/bin/xvkbd -xsendevent -text "\[Alt_L]\[Right]""
  m:0x0 + b:9
```

---

