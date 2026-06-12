---
title: "Can't get scanner working: Canon 3500 series"
date: 2014-11-01
forum: General Help
---

### Post by afrohippie82 on 2014-11-01
How do I get the scanner working on my Canon 3500 series device?

---

### Post by pdc on 2014-11-02
Canon supply their own programme called [COLOR="#0000FF"]ScanGearMP[/COLOR] to run the scanner; programmes such as xsane and simple scan instead use the open source engine called sane 

go here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html?r=s&q=](http://support-asia.canon-asia.com/contents/ASIA/EN/0100552102.html?r=s&q=) and click to Download and Save the file, which is scangearmp-mg3500series-2.20-1-deb.tar.gz

________________

open a terminal; use your Dash search function to find it if you don't know how

____________

next I will list some commands that you copy from here; and paste into the terminal; to paste into the terminal, I suggest using your mouse and the menu line at the top of the terminal;

here are the commands: paste them line by line; hitting the ENTER key after each paste ..........

```
cd Downloads
tar -zxvf scangearmp-mg3500series-2.20-1-deb.tar.gz
cd scangearmp-mg3500series-2.20-1-deb
./install.sh
```

that should install the drivers

______________

to run [COLOR="#0000FF"]ScanGearMP[/COLOR], paste or type this command into the terminal > [COLOR="#FF0000"]scangearmp[/COLOR]

_________________

thereafter one can set up a launcher............to launcher [COLOR="#0000FF"]ScanGearMP[/COLOR] ........

one way I can suggest is to paste these commands

> [COLOR="#FF0000"]sudo apt-get install gnome-panel[/COLOR]

then 

> [COLOR="#FF0000"]gnome-desktop-item-edit ~/Desktop/ --create-new[/COLOR]

that gives you a window as in the attached image: the command must be > scangearmp but you can choose everything else ............

---

### Post by Bucky Ball on 2014-11-02
@pdc: Nice. I have changed your first coloured code font and put it in a code box. Please do the same with the other, please. You can look at how I did the first one or you can follow the last link in my signature for a couple of options for creating them. (Just remove the colour tags and change the quote tags [code] tags.)

---

### Post by afrohippie82 on 2014-11-06
This is awesome thanks for the help as soon as i get this running or if i run into issues i will let you know

---

### Post by afrohippie82 on 2014-12-13
works like a champ!

---

### Post by pdc on 2014-12-13
great! Enjoy

as you started the thread, you can go into Thread Tools and click on the SOLVED button .........nice for people to see it all works ...............

---

