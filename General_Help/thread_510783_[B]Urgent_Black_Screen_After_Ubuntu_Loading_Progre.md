---
title: "[B]Urgent Black Screen After Ubuntu Loading Progress Bar[/B]"
date: 2007-07-27
forum: General Help
---

### Post by designwiz on 2007-07-27
I have seen alot of similar posts but i still cannot find real good solution! I apologize for posting a similar 
thread

My system specs are
Core2Duo T5500 @ 1.66
2GB Ram @ 667 Mhz
Nvidia GeForce Go 7400 Turbocache

After installing nvidia-glx drivers and updates( sudo apt-get build essential etc) 
I installed beryl, Everything was working smoothly(say for 5days) and then yesterday its just wouldnt procced after the loading progress bar!

All i see is a black screen with the cursor wait symbol. I tried pressing ctrl+alt+f1 and then i logged in using the user name and passwd.. tried copying the xorg_backup file still dint work..

tried restarting gdm after killing x, it still wouldnt wrk

then i tried metacity in the console and it came up wit this interesting response
> Window Manager Error: "" found in configuration database is not a valid value for keybingin "toggle_shaded"
Window manager error:Unable to open X display

I have also removed beryl and all its associated files.

Thanks in advance.Any Help would be greatly appreciated. Regards Leo J.

p.s also tried login as root from recovery mode ran startx then in the terminal ran gconf2 went to apps>metacity>windowskeybinding>toggleshaded disabled, it still doesnt work

---

### Post by designwiz on 2007-07-27
Is it a bug? i think its something to do with keyboard binding.. it was working all kewl till yesterday!

---

### Post by Koybe on 2007-07-28
When you hit CTRL+ALT+F1 and log, put in this command:

```
sudo dpkg-reconfigure xserver-xorg
```Follow the instructions, leave by default if you're not sure, and be careful with the monitor configuration, choose easy or medium when asked.

```
sudo /etc/init.d/gdm restart
```

---

### Post by designwiz on 2007-07-29
Thanks koybe really appreciate your help!

Well i doubt reconfiguration the xorg file would help ( I tried it with the rite config)

also let me add something to my problem

1.At the grub i choose the Ubuntu os
2.It shows the ubuntu loading bar and then after that a black screen followed by a wait symbol( the pallate symbol)
3. Now here i tried pressing ctrl+alt+f1 to go to CLI tty1 its asks for login and passwd
4. i enter the username and paswd in the cli mode its logs me in
5. then i enter startx or gdm it works perfectly fine
6. Infact even beryl works fine, so what i see is the problem may lie with the login window
7. I begin to think when i modified the login window option and then it struck me that before this problem arised i had checked the option Restart X window everytime at login!

I am guessing this could be the underlying problem, though unchecking it still dint solve the problem! Guess i need to get the os running soon, might have to reinstall it!

One more question, everytime i reinstall ubuntu i have to do the updates using synaptics/apt-get which is aroung 200mb-400mb instead can i download these updates and store them on hdd so that i can reinstall it from hdd rather than from the net?( my net connection sucks 6-8kbps download!)

I hope we can find a solution. Thanks koybe for your help!. Regards

---

