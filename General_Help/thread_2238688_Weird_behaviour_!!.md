---
title: "Weird behaviour !!"
date: 2014-08-09
forum: General Help
---

### Post by Ifaistos on 2014-08-09
I had a fully functional Ubuntu Unity, just a few minutes ago.

As I was typing and trying to do smt on my computer, I accidentally hit one or the top keys on my keyboard.
Most probably the one that orders the PC to Turn off.

Anyway what happened is that my comp stopped working, the gui disappeared and I got a terminal screen asking me to login...
I pressed Ctrl-C, and it kinda rebooted but in a weird way.

I was again on the GUI login screen, but in a obviously different resolution!! 
I typed in my password and pressed Enter.

Accepted and then all that happens is I see the background image (in this different resolution), my mouse is working and NOTHING else !!

I am just staring at my background, playing with my mouse... 
Tried different key combinations and nothing happens!

I hard rebooted, and I get the same...
Different resolution, login screen, enter password, and then background image and a working mouse...

How do I "reset" this situation?
It has never happened in the past!

Any suggestions?
Please help..!!

---

### Post by Jesse_Campton on 2014-08-09
> [COLOR=#000000]Anyway what happened is that my comp stopped working, the gui disappeared and I got a terminal screen asking me to login...[/COLOR]
[COLOR=#000000]I pressed Ctrl-C, and it kinda rebooted but in a weird way.[/COLOR] This is another terminal (non-gui), you enter this normally by holding down Ctrl+Alt+F1-F6 keys... Ctrl+Alt+F7 will take you back to your Desktop (Gui). With that said, lets try to reset your desktop and Unity, using that method. Hold Ctrl+Alt+F1 > type your login and hit enter > now type your password and press enter (Password will not display any characters when typed). Type this into the terminal: ```
[COLOR=#453E3E][FONT=arial]sudo apt-get install dconf-tools[/FONT][/COLOR]
``` ```
[COLOR=#453E3E][FONT=arial]dconf reset -f /org/compiz/[/FONT][/COLOR]
``` ```
[COLOR=#453E3E][FONT=arial]setsid unity[/FONT][/COLOR]
``` ```
[COLOR=#453E3E][FONT=arial]unity --reset-icons[/FONT][/COLOR]
``` , now type: ```
sudo reboot
``` and press enter.

---

### Post by Ifaistos on 2014-08-09
Thank you for your answer.

You know it could be that I pressed smt like that...
I remember I was trying to make Chrome refresh by pressing Ctrl-F5... so it could be smt that got mixed up there...

Anyway...

I followed your advice but at the command dconf reset -f /org/compiz/
I got the following error :

**error : Cannot autolaunch D-Bus without X11 $DISPLAY**

---

### Post by Jesse_Campton on 2014-08-09
[SIZE=3]**Borrowed this from another thread:**[/SIZE] [B][COLOR=#000000][FONT=verdana]Hi, here is what you need to do.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]You can reset unity or compiz or both by doing the following.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Open a terminal by hitting ctrl+alt+t or alt+f2, if one of those key combination does not open the terminal try ctrl+alt+f1 thru f6. Then type this command in terminal to reset unity. [/FONT][/COLOR][/B]

[COLOR=#000000][FONT=verdana]Unity --reset 

**Use these commands to reset all the settings in compiz.**[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]gconftool-2 --recursive-unset /apps/compiz[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]gconftool-2 --recursive-unset /apps/compiz-1[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]gconftool-2 --recursive-unset /apps/compizconfig-1 [/FONT][/COLOR]
[B][COLOR=#000000][FONT=verdana]let unity reset run for about 3 minutes then restart your computer and do not worry about the errors.[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]Thank you

Borrowed from : [/FONT][/COLOR][/B][http://ubuntuforums.org/archive/index.php/t-1845356.html](http://ubuntuforums.org/archive/index.php/t-1845356.html)

---

### Post by Ifaistos on 2014-08-09
Thank you for your answer :-)

unity --reset function is a deprecated command.. is not supported anymore :(

---

### Post by Ifaistos on 2014-08-09
I run the gconftool-2 commands ...

there were no errors...

I rebooted but nothing changed. :(

---

### Post by Jesse_Campton on 2014-08-09
Lets try this, follow the steps in this Tutorial for resetting Unity in 14.04: [http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html](http://www.webupd8.org/2012/10/how-to-reset-compiz-and-unity-in-ubuntu.html)

---

### Post by Ifaistos on 2014-08-09
ok..

but what should I do with the command :
dconf reset -f /org/compiz/

It produces the error I am talking about above....
So should I just skip it?

---

### Post by Ifaistos on 2014-08-09
I believe I have found smt interesting..
I tried to run the command 
unity
from the terminal...

it stopped with the following error :
Compiz (core) - Error: Plugin 'opengl' not loaded.

and then it froze...

I think that this is the reason that even in the weird resolution I just see my background image... It tries to load unity and it can't...
I think I "broke" unity somehow !!

How can I reinstall it?

---

### Post by Jesse_Campton on 2014-08-09
Ifaistos, If the Unity reset does not work, I found another possible solutions to your problem here, [http://askubuntu.com/questions/457501/upgrade-from-13-10-to-14-04-no-unity-dash-for-default-user-special-compiz-config](http://askubuntu.com/questions/457501/upgrade-from-13-10-to-14-04-no-unity-dash-for-default-user-special-compiz-config) , The user seemed to have fixed it using: [COLOR=#333333][FONT=UbuntuRegular]L.L.E. I fixed it, I don't know if it helps anyone but, what I did was to reinstall the compiz-core:[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
sudo apt-get install --reinstall compiz-core[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]and then to remove the files in the .cache and .config folders[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]sudo rm -rf ~/.config/dconf/user sudo rm -rf ~/.cache/compizconfig-1[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Hope this helps others![/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Thanks for the support![/FONT][/COLOR]

---

### Post by Ifaistos on 2014-08-09
It didn't work :(

I am downloading ubuntu 14.04, and I have formated a usb stick on my windows computer.

---

### Post by Jesse_Campton on 2014-08-09
Sorry Ifaistos, Trial and error I guess.

---

### Post by Ifaistos on 2014-08-09
yeah.. I understand.. you did your best.. 
Thank you !! :)

---

