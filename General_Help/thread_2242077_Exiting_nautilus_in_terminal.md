---
title: "Exiting nautilus in terminal"
date: 2014-08-30
forum: General Help
---

### Post by Liamdale on 2014-08-30
Hi,

To install new fonts, I opened nautilus in superuser mode.  The fonts installed, I tried to quit nautilus but the commands found on the web do not seem to work.

Is there a graceful way of closing the nautilus window from the terminal.

The commands I used:

To execute nautilus :  gksu nautilus  Works fine

To try and close nautilus from terminal after work completed:  nautilus -q  -  does not work
killall nautilus  -  does not work
pkill nautilus  - does not work

All these commands were found on the web.  If closed the nautilus window (s) and then the terminal window it works but I get a message asking me I want to kill all the processes.

Does not seem like the best method to exit nautilus.

Liamdale

---

### Post by sbnwl on 2014-08-30
```
If closed the nautilus window (s) and then the terminal window it works  but I get a message asking me I want to kill all the processes.

Does not seem like the best method to exit nautilus.
```

That is still a graceful way.

Or try with sudo, as you had opened the nautilus window as root user
```
sudo killall nautilus
```

---

### Post by Liamdale on 2014-08-30
Hi,

I tried "sudo killall nautilus".  I tried all the previous commands with the sudo prefix but without any result.

---

### Post by ajgreeny on 2014-08-30
There are better ways to install fonts, as well; no need to use nautilus as root to do something like that.

First make a folder to hold your custom fonts.
```
sudo mkdir /usr/share/fonts/truetype/myfonts
```

Next open a terminal in the folder where you have fonts to install and use command
```
sudo cp ./*.ttf /usr/share/fonts/truetype/myfonts
```
This will copy the truetype fonts to that folder. You may need to do this separately for any named fonts where the file suffix .TTF is in upper case, as linux is case sensistive.

Now open a terminal in your myfonts folder and use command
```
sudo fc-cache -f -v
```
to update the fonts database and install the fonts so that both your applications like LibreOffice, and any other users including the system utilities can use them.

---

### Post by mc4man on 2014-08-30
The behavior of gksudo nautilus can be different depending on what version of nautilus & what release of Ubuntu

Here on 14.04 I generally don't use as I have nautilus with pkexec enabled but in any event - 
Best is not to use a terminal at all, just go > Alt+F2 > gksudo nautilus

If using from a terminal then you can close the terminal at any time after running the command, the root nautilus window will not close
(- can be seen with command of 
gksudo nautilus & quit

---

### Post by Liamdale on 2014-08-30
Thanks mc4man;

Tried your suggestion and it's much easier.  Will go this route in the future.  Also after my post I kept experimenting with the "gksudo nautilus" command and have found that if I closed the nautilus window it exited automatically in the terminal.  I can only assume I had another window open before I closed the terminal.  I will mark thie post as solved.

Thanks everyone !

---

### Post by Liamdale on 2014-08-30
Thanks ajgreeny;

Your method is much more to the point.  One question.  The new fonts which I downloaded were copied to my /usr/share/fonts/truetype folder became available immediately.  Why must I use sudo fc-cache -f -v.

(note.  This is the second post for this reply. seems my first one did not work)

---

### Post by ajgreeny on 2014-08-30
**fc-cache**  scans  the  font  directories on the system and builds font information cache files for applications using fontconfig for their font handling.  See **man fc-cache** in terminal for info.

I have no idea what happens if you don't run that command as I have always done so, but if you have just a single user on a machine you can put the ttf or TTF files into a hidden .fonts folder in your home and they will be available to you, but not to any user you subsequently add, nor to any root/system applications.

---

### Post by Liamdale on 2014-08-31
Thanks ajgreeny;

I will add this command to my work habits.  Interesting about adding fonts to the home file but in my case of little use.

---

