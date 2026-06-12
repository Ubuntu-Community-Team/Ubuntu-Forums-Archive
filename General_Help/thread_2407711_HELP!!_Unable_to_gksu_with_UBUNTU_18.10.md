---
title: "HELP!! Unable to gksu with UBUNTU 18.10"
date: 2018-12-07
forum: General Help
---

### Post by maravingian on 2018-12-07
HI,

Its been a while since I last posted, but i never realised how much the architecture of Ubuntu 18+ has been!!

I`m trying to create a file within a directory and add a line to allow my Scrol Lock to cause my keyboard to light up.  I`ve been following a really good post on how to do this but i am now stumped at the point where i need to gksudo gedit the file.  As gksudo is no more i have forgotten how to edit the file.  I have tried sudo gedit but when i go into gedit, i am advised that i do not have permission to change anything.

***[SOLVED] keyboard back light ***- this is the thread i was following.  So far I`ve found something about pkexec but i cant seem to edit the file to add in the pkexec privilleges.

Please can anyone enlighten me??

Many Thanks :)

---

### Post by CatKiller on 2018-12-07
I don't know what it's changed to, either, but ```
sudo nano
``` will give you a command line text editor as root.

---

### Post by maravingian on 2018-12-08
So i copied the Xmodmap template and added in mod3 = Scroll_Lock but istill cant seem to get the keyboard backlight working.  Is there any way i can open the saved file in nano?  Further down the keyboard backlight thread it showed the below code. Where can i enter this code?

#! /bin/bash
#num - 0, caps - 0, scroll - 0    LED mask:  00000000
#num - 0, caps - 1, scroll - 0    LED mask:  00001001
#num - 1, caps - 0, scroll - 0    LED mask:  00000002
#num - 1, caps - 1, scroll - 0    LED mask:  00001003
#num - 0, caps - 0, scroll - 1    LED mask:  00000004
#num - 0, caps - 1, scroll - 1    LED mask:  00001005
#num - 1, caps - 0, scroll - 1    LED mask:  00000006
#num - 1, caps - 1, scroll - 1    LED mask:  00001007
leds=`xset q | grep LED | cut -c66`
case $leds in
0 | 1 | 2 | 3 )
xset led 3 ;;
4 | 5 | 6 | 7 )
xset -led 3 ;;
esac

---

### Post by howefield on 2018-12-08
Yes, use the path to the file that you want to edit, in the command, eg..

```
sudo nano path_to_file
```

---

