---
title: "Missing menu bar"
date: 2014-05-01
forum: General Help
---

### Post by gerry-liebling on 2014-05-01
I just updated to 14.04, and upon restarting the top menu bar is missing.  I cannot get any applications to fix any settings, nor can I do a reinstall.  Control-Alt-T does not give me a terminal window to access settings.  HELP.

---

### Post by grumblebum2 on 2014-05-01
When your at the blank desktop, If you can get to tty1 using ctrl+alt+F1
login and run
```
export DISPLAY=:0
```
```
dconf reset -f /org/compiz/
```
Then run 
```
sudo reboot
```

---

### Post by gerry-liebling on 2014-05-02
Thanks for the suggestion, but it didn't help.  I did the steps you suggested, but still have no menu bar.

---

### Post by ibjsb4 on 2014-05-02
Go to tty and try:

```
sudo apt-get -f install
```

This command will attempt to fix any broken packages.

---

### Post by grumblebum2 on 2014-05-02
> **gerry-liebling said:**
> Thanks for the suggestion, but it didn't help.  I did the steps you suggested, but still have no menu bar.

Do you get a pop-up menu when you right click on the desktop?

---

### Post by gerry-liebling on 2014-05-02
Thanks again for the suggestions.  Running apt-get -f install did not help.  Yes, I do get a pop-up menu with a right mouse click.  My desktop displays OK.  Some apps, like fotoxx no longer work, but I can deal with that later, once I get my menus back.

---

### Post by grumblebum2 on 2014-05-02
As  a start, get a terminal on the desktop.
Right click and create a new folder.
Open the folder and navigate to **/usr/share/applications**
Find the "Terminal" launcher and copy it to your desktop.

Firstly I would update and look for errors.
```
sudo apt-get update && sudo apt-get upgrade
```
Then do a logout/login test.

What you can also try is to create a new user account.
Doing this will tell you if there is some setting in your home folder causing the problem.
In the terminal...
```
unity-control-center user-accounts
```
Create a new administrator account and then logout and into the new account.

---

### Post by gerry-liebling on 2014-05-02
Run the update and upgrade commands.  Report was that there were no updates or upgrades, and the menu bar is still missing.

Created new admin account, logged into it - no change - menu bar still missing.  I'm beginning to think that an entire new 14.04 reinstall is warranted.

---

### Post by gerry-liebling on 2014-05-02
Did a complete reinstall of 14.04 with no change.  I have tried logging in with the three different window managers - GNOME Flashback (Compiz), GNOME Flashback (Metacity), and Ubuntu.  All three come up without the menu bar, but all three start up displaying the CompizConfig Settings Manager.  Is it trying to tell me that there is a problem with my settings?  What settings might be at fault?

---

### Post by ibjsb4 on 2014-05-02
Are you running the proper monitor resolution and frequency?  In terminal:

```
xrandr
```

[http://ubuntuforums.org/showthread.php?t=884157](http://ubuntuforums.org/showthread.php?t=884157)

---

### Post by gerry-liebling on 2014-05-02
Thanks for the suggestion.  Tried it - got:

Screen 0: minimum 320 x 200, current 1680 x 1050, maximum 4096 x 4096
VGA-1 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected primary 1680x1050+0+0 (normal left inverted right x axis y axis) 430mm x 270mm
   1680x1050      59.9*+
   1280x1024      75.0     60.0  
   1152x864       75.0  
   1024x768       75.1     60.0  
   800x600        75.0     60.3  
   640x480        75.0     60.0  
   720x400        70.1  
TV-1 disconnected (normal left inverted right x axis y axis)

I was wondering if this might be related to the problem since my desktop seems a little stretched, but the system will not let me increase the resolution from the current 1680x1050, and decreasing it only exaggerates the stretch.

---

### Post by ibjsb4 on 2014-05-02
Unless you have a big square monitor, I don't think xrandr is detecting it.  Try resetting xorg.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Additional resolutions can be added.

[https://wiki.archlinux.org/index.php/xrandr#Adding_undetected_resolutions](https://wiki.archlinux.org/index.php/xrandr#Adding_undetected_resolutions)

[http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution](http://askubuntu.com/questions/377937/how-to-set-a-custom-resolution)

[http://www.google.com/search?client=qupzilla&q=add%20resolution%20to%20xrandr](http://www.google.com/search?client=qupzilla&q=add%20resolution%20to%20xrandr)

Most monitors also have adjustments.  What is your screen size?

---

### Post by gerry-liebling on 2014-05-02
I seem to have a partial solution - at /usr/share/applications there is a launcher "panel".  Clicking on this restores the top menu bar, but it is not permanent.  On restarting the menu bar is still missing until I again click on "panel."  And, on restarting, the CompizComfigSettingsManager always comes up.

---

### Post by gerry-liebling on 2014-05-02
Reset xorg.  xrandr gave the same results.  My monitor is a Dell, 20" diagonal, 17" wide x 10.75" high.

---

### Post by grumblebum2 on 2014-05-02
Also won't hurt to check some things and have the info.

Check in ccsm thet the unity plugin is enabled.

Install wmctrl...
```
sudo apt-get install wmctrl
```

Then run this to give your current session and window manager in use....
```
echo $DESKTOP_SESSION && wmctrl -m | awk '/Name:/{print $2}'
```

Your gfx drivers....
```
lspci -nnk | grep -iA2 vga
```

Unity support test...
```
/usr/lib/nux/unity_support_test -p 
```


PS: You can start the "panel" with **gnome-panel**
and **gnome-session-properties** will show startup applications.

---

### Post by gerry-liebling on 2014-05-02
Adding gnome-panel and gnome-wm to the startup applications seems to have solved the missing menu problem.  But I still get the CompizConfigSettingsManager on startup.  Not a big problem but a nuisance.

---

### Post by Norway719 on 2014-05-03
Thanks for the help. I had an identicle issue when I upgraded to 14.04. (It restarted during the upgrade and would not boot up at all. I had to do a live disk and run boot repair...) Once that was fixed up, it appeared that unity didn't work(I think?) because the applications bar on the left, bar on to of the screen as well as the bars on top of windows were missing. I had to left click to pull up any windows as was discussed above...

At any rate
ATTN: grumblebum2, I performed the operations that you documented in post #2 of this thread and it worked. Thank you much for your help!

--Norway

---

### Post by gerry-liebling on 2014-05-05
I would like to close this thread as Solved, but I first have a couple of questions that I hope can be answered:

1. My problem of the missing menu bar (and a few other erratic problems with the mouse) was solved by adding 
      env XDG_MENU_PREFIX="gnome-f
          and
      gnome-wm
   to the startup process list.  I never had to do this before.  Why now?

2. The CompizConfig Settings Manager comes up on booting, before the desktop is displayed.  It is not in the startup process list.  Why is it starting and how can I get rid of it?

Thank you.

---

