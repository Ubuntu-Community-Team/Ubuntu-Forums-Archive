---
title: "What solution for avoid xscreensaver working with video and games ?"
date: 2021-10-06
forum: General Help
---

### Post by aug7744 on 2021-10-06
Xscreensaver is configurated for few minutes blank screen.
If using keyboard and mouse xscreensaver work correctly not loading screen saver, but if running a game using game controller and videos in full screen is loaded screen saver.
What is the solution for fix it ?

Have a nice day.

---

### Post by TheFu on 2021-10-06
Either disable the screen saver or change the config so that it turns on after a longer period.

I disable it before and re-enable it after:
$ more blank_screen.sh 
```
#!/bin/bash

# ###########################################################
while getopts 'yn' OPTION
do
  case $OPTION in
  y)    xset s off &
        xset -dpms &
        xscreensaver-command -exit
        echo "Screen Blanking Disabled"
        ;;
  n)   xset +dpms &
       xset s on &
       xscreensaver &
       xscreensaver-command -activate
       echo "Screen Blanking Enabled"
        ;;
  esac
done
```

This is all X11 specific. It won't work with Wayland.

---

### Post by aug7744 on 2021-10-07
Thanks for help me.
I not want manually disable screensaver for a longer period.
Xsreensaver work with keyboard, but not with game controllers and video player being a problem need fix.
I want install Ubuntu in other machine , but users seeing that problem will avoid switch to another OS.

---

### Post by TheFu on 2021-10-07
xscreensaver has been around 40 yrs. It is for X11. Gaming isn't really a core use of a screensaver.
You can easily wrap the program that starts the game you want with a 
```
blank_screen.sh  -y
/program/to/run/game
blank_screen.sh  -n
```
And never think about it again.  Linux isn't like other OSes.  We can handle trivial issues - or things we see as issues - ourselves. It is expected.

---

### Post by ajgreeny on 2021-10-07
Are you using Ubuntu or one of the other DE versions?
If using Xubuntu it is possible to right click on the power-manager icon in the panel and choose **Presentation Mode** which turns of both the screensaver, if you have one, and power-manager for the duration until you deselect the Presentation Mode setting, stopping any interruption of the display.

OK, it's a manual setting, but in my opinion it is another of the great advantages of Xfce over gnome; unless, of course, gnome can do something similar?

---

### Post by aug7744 on 2021-10-07
@TheFu

"xscreensaver has been around 40 yrs. It is for X11."
Thanks for information :-)

"Gaming isn't really a core use of a screensaver."
Not. I only wait when happen input from game controller or watching videos xscreensaver not start the screensaver.
I not wait run screensaver with games. That is really madness.

"You can easily wrap the program that starts the game you want with a "

blank_screen.sh  -y
/program/to/run/game
blank_screen.sh  -n

What exactly does it ? Is lines to create a script ?

"And never think about it again. Linux isn't like other OSes. We can handle trivial issues - or things we see as issues - ourselves. It is expected."
Oh yes ... for some problems using commands lines or trying information not is exactly a problem, but try install OS for some users where has problems in example the screensaver running when playing videos does others users avoid use and the worst detail users that not understand about Linux Ubuntu spreading wrong information and saying to avoid switch from other OS.
I had information about how good is Linux, but I not had switched because "all time" anyone here and where saying about few softwares available for Linux and thus I having a machine running all that I want to use not had done a try in test Ubuntu.
Today I see how LESS problems happen in Linux. The only few problems are in example that issue with xscreensaver and for some problems need figure being hard to find a information or solution.

@ajgreeny

"Are you using Ubuntu or one of the other DE versions?"
Lubuntu.

"If using Xubuntu it is possible to right click on the power-manager icon in the panel and choose Presentation Mode which turns of both the screensaver, if you have one, and power-manager for the duration until you deselect the Presentation Mode setting, stopping any interruption of the display."
I want xscreensaver disabling automatically. Thus I will install Ubuntu in others machines for users that not wait tweak or commands.

"OK, it's a manual setting, but in my opinion it is another of the great advantages of Xfce over gnome; unless, of course, gnome can do something similar?"
Xfce look really great.

Thanks for all replies.

---

### Post by aug7744 on 2021-10-17
The solution
[https://github.com/Tookmund/config/blob/master/xscreensaverstopper.sh](https://github.com/Tookmund/config/blob/master/xscreensaverstopper.sh)

Thanks for all replies.
Have a nice day.

---

