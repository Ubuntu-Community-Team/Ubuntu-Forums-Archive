---
title: "[Solved] How to extended display on dual monitor on Xubuntu 12.04 LTS"
date: 2013-07-01
forum: General Help
---

### Post by arifalisyed on 2013-07-01
Hello There,
                 I Recently installed Xubuntu 12.04 LTS on my Dell Precision 1650 desktop( it has Nvidia Card).
It Ubuntu certified desktop.  I have added another monitor to this deksotp on DVI port. 
But i dont see any option to extend display i have attached the screenshot of "Settings->Display", all i can do is set the resolution for both.

Earlier  when i had added second monitor on VGA port , it dint work. After i pluggin into DVI port its detecting it but I am getting the identical display on  both, [U][B][COLOR=#b22222]while i want to extend my display.
[/COLOR][/B][/U]


Another point ( if its important) I have connected the second monitor using a DVI splitter cable, I am not sure if that makes any difference.

 

[ATTACH=CONFIG]244291[/ATTACH][ATTACH=CONFIG]244292[/ATTACH]

---

### Post by Toz on 2013-07-01
Proper multi-monitor support isn't available in the version of Xfce that comes with 12.04, so you'll have to use arandr. Look for it in the software centre or, from a terminal window:
```
sudo apt-get install arandr
```

Once installed, you'll find it in the Settings Manager. Double-click to start it up. Drag the monitors to position them how you would like them then Layout->Apply.

To make it permanent (so you don't have to run arandr everytime you login):
1. Layout -> Save As (select a name, default save directory is ~/.screenlayout)
2. Create a startup entry (Settings Manager -> Session and Startup -> Application Autostart) where the command will be:
```
/home/<USER>/.screenlayout/<FILE>
```
...where <USER> is your username and <FILE> is the filename you gave in the previous step.

---

### Post by Jhon smith on 2013-07-01
Using  PPA, in the Xfce Settings Manager.  select the position of each monitor you  want to mirror the displays or not.
The PPA currently provides Thunar 1.5.x, Xfce4 Settings and Axo development builds. To add the PPA and upgrade these packages in Xubuntu 12.10 or 12.04, use the commands 
:osudo add-apt-repository ppa:xubuntu-dev/xfce-4.12
sudo apt-get update
sudo apt-get upgrade

Once the packages have been successfully upgraded, open the Settings Manager, and under "Display", uncheck the "Mirror displays" option to extend your display to the external monitor.

---

### Post by arifalisyed on 2013-07-01
Thanks  Toz, [COLOR=#000000][FONT=Ubuntu Mono]arandr worked for me.

Thanks Jhon Smith.[/FONT][/COLOR]

---

### Post by Toz on 2013-07-01
Glad to hear it worked.
Can you please mark this thread as solved:
1. Click the "edit" link on your first post
2. Click the "Go Advanced" button
3. Change the prefix to "[SOLVED]"
4. Save
Thanks.

---

### Post by arifalisyed on 2013-07-05
@Roz. Done

However  the display quality is not great with this tool.

---

### Post by Toz on 2013-07-05
> **arifalisyed said:**
> However  the display quality is not great with this tool.
If by "display quality" you mean the resolution is less than ideal, you can set a different resolution for each display by right-clicking the display's box in arandr and selecting a different resolution.

---

