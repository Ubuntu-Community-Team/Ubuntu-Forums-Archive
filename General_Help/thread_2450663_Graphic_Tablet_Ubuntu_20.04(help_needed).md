---
title: "Graphic Tablet Ubuntu 20.04(help needed)"
date: 2020-09-18
forum: General Help
---

### Post by nexubu on 2020-09-18
Hello there, I am new Ubuntu user. I switched from Windows 10 to Ubuntu 20.04 for stability and performance.
I work(hobby) in Unity3D and usually draw my sprites via graphic tablet.  But after i switched from windows to Ubuntu , i noticed my tablet  doesn't work properly its not a Wacom Tablet its 10moons 1060Plus  Graphic Tablet 10x6 Inch Digital Drawing (Gotop Information Inc. [T501]  Driver Inside Tablet). Generaly tablet kinda works ,pressure sensitivity  works but its only mapping half of my tablet and when i draw circle its  eclipse it feels like on X axis pen is moving easily and on Y axis it  moves kinda slow... Half of my tablet is the entire screen. I tried to  google some fixes how can i modify mapping space but i only found  commands for wacom tablets.

When i type xinput in terminal i can see under Virtual core pointer there are
SZ PING-IT INC. [T501] Driver Inside Tablet Mouse id=17 [slave pointer (2)]
&#9116; &#8627; SZ PING-IT INC. [T501] Driver Inside Tablet Consumer Control id=24 [slave pointer (2)]
&#9116; &#8627; SEM USB Keyboard Consumer Control id=28 [slave pointer (2)]
&#9116; &#8627; SZ PING-IT INC. [T501] Driver Inside Tablet Pen (0) id=30 [slave pointer (2)]

i found this driver on github
[https://github.com/DIGImend/10moons-tools](https://github.com/DIGImend/10moons-tools) does anyone know step by step how to install the driver? How do i Build with autoreconf -i -f && configure && make.?
I would really appreciate any help i can get.

---

### Post by dino99 on 2020-09-18
Needs identification via 'lsusb' first
Also grab error (red line) or warning (yellow line) about that tablet inside 'journalctl -b' terminal output.

System Settings have to find/identify this hardware too.

---

### Post by nexubu on 2020-09-18
Bus 003 Device 003: ID 08f2:6811 Gotop Information Inc. [T501] Driver Inside Tablet



[https://imgur.com/a/tpXeKKr](https://imgur.com/a/tpXeKKr) 

keep in mind i am total noob when it comes to ubuntu. xD

---

### Post by drpjkurian on 2020-09-18
I remember a Ubuntu member who helped to solve intricate issues of graphic tablets for all those who sought help. His username is [Favux]("https://ubuntuforums.org/member.php?u=699990"). He is inactive now. You may wake him by sending a personal message(If you are lucky).
By the way, I feel the solution might be editing the X and Y coordinates in the configuration file.

---

### Post by nexubu on 2020-09-18
Thank you for replying i sent him a pm... 
Yeah i feel by editing x and y coordinates that might be the solution only if i knew where is that configuration file or if i knew how to locate it. xD

---

### Post by nexubu on 2020-09-18
i found this... 

[https://imgur.com/a/2k1o2Bh](https://imgur.com/a/2k1o2Bh)

---

### Post by drpjkurian on 2020-09-18
Hi
I'm not sure about this solution, but you may try changing the 'scale' to the size of the screen you have and give a try.

---

### Post by nexubu on 2020-09-18
in my original post there is github link with the driver for setting up the tablet. but actually i don't know how to install it. 

here is the read-me file 

         [h=1][]("https://github.com/DIGImend/10moons-tools#10moons-tools")[/h]
[h=1]10moons-tools[/h] 10moons-tools is a collection of tools for enabling and inspecting 10moons tablets. So far it has only one tool: 10moons-probe.
 Build with autoreconf -i -f && configure && make.
 10moons-probe is a quick and dirty tool for enabling full functionality of 10moons tablets (however much there is).
 Execute like this:
 sudo ./10moons-probe <BUS> <DEV>
 Where <BUS> is a USB bus number, and <DEV> is a device address.
 So, if your tablet was represented by this line in the lsusb output:
 Bus 002 Device 038: ID 08f2:6811 Gotop Information Inc.
 You can run 10moons-probe like this:
 sudo ./10moons-probe 2 38


how should i install this anyone have a clue only thing i do know is to type last command sudo ./10moons-probe 2 38 but thats the last step ?

---

### Post by drpjkurian on 2020-09-18
Hmmm
Let us give a try!
Download the zip files by clicking the 'code' button. Extract it to your home folder. Enable all the files as 'executable'.
Open the extracted folder in terminal (right click and select 'open in terminal'). 
Execute the command ```
autoreconf -i -f && configure && make
```
and ```
sudo ./10moons-probe <BUS> <DEV>
```.
Hope you know the BUS and DEV.
and finally execute the last command.
Restart the machine.
It will work if you are lucky!!!
Best wishes!

---

### Post by nexubu on 2020-09-18
[**[COLOR=#000000]drpjkurian[/COLOR]**]("https://ubuntuforums.org/member.php?u=805294") thank you for all the help... i asked the developer of that stuff and he said that that is not a driver ...it's a development tool.


i found this also this should be some kinda driver, i tried to install it but it failed 
[https://github.com/alex-s-v/10moons-driver](https://github.com/alex-s-v/10moons-driver)
i installed all the req 
[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]pyusb==1.0.2[/TD]
       [/TR]
       [TR]
         [/TR]
[/TABLE]
PyYAML==5.2[TABLE="class: highlight tab-size js-file-line-container"]
[TR]
[TD="class: blob-code blob-code-inner js-file-line"]evdev==1.2.0[/TD]
       [/TR]
[TR]
         [/TR]
[/TABLE]

and when i run 
sudo python driver.py it said 

File "driver.py", line 6, in <module>from evdev import UInput, ecodes, AbsInfoModuleNotFoundError: No module named 'evdev'

---

