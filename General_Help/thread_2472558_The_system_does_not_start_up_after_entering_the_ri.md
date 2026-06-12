---
title: "The system does not start up after entering the right password"
date: 2022-03-03
forum: General Help
---

### Post by limlleonard on 2022-03-03
Hallo,

I have a lenovo z50-70 laptop with Ubuntu 21.XX installed. I tried to install chinese input with fcitx (It is my speculation, it would be because of other reason). After the package installed, I restart the computer, input the password, then I can only see the mouse but the screen is black. If I turn off the power, I could go to the recovery mode. As suggested in internet, I tried dpkg and grub options, fsck I couldn't because I don't know how to go to read-only mode.

Is there any way to recover it?

Thanks

---

### Post by #&amp;thj^% on 2022-03-03
> **limlleonard said:**
> Hallo,

I have a lenovo z50-70 laptop with Ubuntu 21.XX installed. I tried to install chinese input with fcitx (It is my speculation, it would be because of other reason). After the package installed, I restart the computer, input the password, then I can only see the mouse but the screen is black. If I turn off the power, I could go to the recovery mode. As suggested in internet, I tried dpkg and grub options, fsck I couldn't because I don't know how to go to read-only mode.

Is there any way to recover it?

Thanks

change back the key board then and try.
> **limlleonard said:**
> Hallo,

I have a lenovo z50-70 laptop with Ubuntu 21.XX installed. **_I tried to install chinese input_** with fcitx
key character/mapping change with different keyboard layouts
This add a bit more ```
localectl status
   System Locale: LANG=en_US.UTF-8
       VC Keymap: us
      X11 Layout: us
```
at grub start you can try grub command line options such as...

 `setkmap=`yourlang'  as a kernel boot option.
or simply

setkmap=yourlang for the grub boot line.

---

### Post by Impavidus on 2022-03-03
That password you enter as the last action before getting a black screen with mouse pointer, is that the password for harddrive encryption (if you have an encrypted system) or simply the login password of your user? In the later case, the system has fully booted, but login fails. You could try to get to the console: ctrl+alt+F3 or one of the other function keys. One of the function keys (usually F7 or F1) should bring you back to the GUI.

In recovery mode, having a read-only filesystem is the default.

The exact version of Ubuntu can be relevant. The difference between 21.04 and 21.10 is larger than the difference between 20.04 and 21.10 (as 21.04 is dead). There is no 21.XX.

---

### Post by vic11con on 2022-03-04
[COLOR=#232629][FONT=-apple-system]Press Ctrl+Alt+F3 and login into the shell.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Now run ls -lA. If you see the line[/FONT][/COLOR]
-rw-------  1 root root   53 Nov 29 10:19 .Xauthority


Also, Did you end up here after running sudo startx?

---

### Post by limlleonard on 2022-03-04
I can go to shell. When I run **ls -lA**, it shows directories and something like .bash_history, .bash_logout, .profile, .sudo_as_admin_successful, .xinputrc, but no .Xauthority.

If I run **sudo startx**, it goes to GUI. But the designs are changed as if I start the system for the first time, my files are still in the right directories though. When I restart the computer, login, it was like the same: the screen is black with a mouse on it.

In the shell, I could not go to GUI by pressing f1 or f7, hot even the blackscreen with mouse.

By the way, the system should be 20.04.

---

### Post by #&amp;thj^% on 2022-03-04
startx runs ~/.xinitrc, you don't have one
**Running "sudo startx" should be forbidden**, The net result is that sudo startx will leave a root-owned .Xauthority in your user's home directory - which the user then cannot write to because of its ownership and permissions, so that startx without sudo fails. More here: [https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications](https://askubuntu.com/questions/270006/why-should-users-never-use-normal-sudo-to-start-graphical-applications)
switch to a virtual terminal using  CTRL+ALT+2 and even if you say you don't have one, run this anyway: "rm ~/.Xauthority"
Also show this please:
```
 printenv | grep HOME
```
This:> If I run sudo startx, it goes to GUI. But the designs are changed as if I start the system for the first time, my files are still in the right directories though. When I restart the computer, login, it was like the same: the screen is black with a mouse on it.
And yes you are right a New freshly Root owned session, is what you saw.

---

### Post by limlleonard on 2022-03-05
press CTRL+ALT+2 or CTRL+ALT+F2 nothing happened
[COLOR=#000000][/COLOR]CTRL+ALT+F3 -> printenv | grep home shows
PWD=/home/ll
HOME=/home/ll

---

### Post by #&amp;thj^% on 2022-03-05
I was hoping to see more along the lines as:
```
me on Sat Mar 05 at 07:42 AM in ~ branch: (HEAD) 
>>  printenv | grep home 
PWD=/home/me
XAUTHORITY=/home/me/.Xauthority
HOME=/home/me


me on Sat Mar 05 at 09:48 AM in ~ branch: (HEAD) 
>> sudo printenv | grep home 
[sudo] password for me: 
XAUTHORITY=/home/me/.Xauthority

```
You see a difference using sudo.
All this changed right after you changed your keyboard layout right?
Show this please:
```
locale
```
And:
```
setxkbmap -query | grep layout
```

---

### Post by limlleonard on 2022-03-05
sudo printenv | grep home
shows nothing (even with my limited linux knowledge, I find it werid)

It happened when I install fcitx package

locale
LANG=de_DE.UTF-8
LANGUAGE=
LC_CTYPE="de_DE.UTF-8"
LC_NUMERIC="de_DE.UTF-8"
LC_TIME="de_DE.UTF-8"
LC_COLLATE="de_DE.UTF-8"
LC_MONETARY="de_DE.UTF-8"
LC_MESSAGES="de_DE.UTF-8"
LC_PAPER="de_DE.UTF-8"
LC_NAME="de_DE.UTF-8"
LC_ADDRESS="de_DE.UTF-8"
LC_TELEPHONE="de_DE.UTF-8"
LC_MEASUREMENT="de_DE.UTF-8"
LC_IDENTIFICATION="de_DE.UTF-8"
LC_ALL=

(sudo) setxkbmap -query | grep layout
Cannot open display "default display"

---

### Post by #&amp;thj^% on 2022-03-05
When you first boot up and at grub hit 'e'
add this
```
setkmap=de
```
from what I see that was your default layout before all this.
hit enter and bootup, can you now login?

---

### Post by limlleonard on 2022-03-06
@1fallen
I did what you suggest. The situation barely changed except, from shell, I can press ctrl+alt+f1 to go back to gui. But if I continue to login, it goes like before, there's only mouse on black screen.

---

