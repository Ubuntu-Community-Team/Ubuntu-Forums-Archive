---
title: "--HELP - How to : -Nvidia Driver and more"
date: 2007-10-30
forum: General Help
---

### Post by bhencetotozo on 2007-10-30
Im sorri for being such a linux newbie,
I had alot of trouble to get where i am now. Linux ubuntu 7.10 Running finally.
Took me 8 hours to findout i had to edit the kernell line ( NOAPIC ) in order to boot.
I have a few questions i'd to know if someone can help me.

My system Hardware:
CPU : Amd Athlon Fx32 Dual Core 2.8ghz
Memory 4 GB ddr2 800mhz
Video card Nvidia Gforce 7950gx pcie
700 WATT power supply 

Question 1:
How to install Nvidia Driver? ...
       ----- What i've done so far... NO SUCSESS
-- downloaded the .run file  from nvidia.com ,
-- i went to console, AS ROOT i typed shutdown now, in maintence mode, i loged as root, typed init 3 , then i did the sh on the .run driver file ....
-- It said i was running on level 1 , then i ignored error and procedded.. then i got an error about couldnt download something from nvidia.com ...

 Question 2 , I how can i get permission to EDIT the main.lst file?
question 3 , what is the command to copy a file from the desktop to the /home directory?
question 4 - how do i install beryl ?? before i do it i need to install the nvidia driver first.

Thank you for the help

---

### Post by bhencetotozo on 2007-10-30
Sorri for interrupting people i dont mena to be rude, but please take your time to help me, a linux newbie.

i have linux ubuntu 7.10 x86 ..
CANNOT install the LINUX driver NOR beryl ... I need help.. I just started.

The motivation i have is that i sucessfully installed adobe flash plugin for firefox after reading on google for 8 hours...

i been reading for 8 days now and i cant figure out how toinstall NVIDIA driver..

Please read my thread [http://ubuntuforums.org/showthread.php?t=597969](http://ubuntuforums.org/showthread.php?t=597969)
and help me. Thank you very much people.

---

### Post by thelocust on 2007-10-30
When you first boot into ubuntu there should be a little pop up to install the nvidia drivers and 7.10 comes with compiz installed so you don't need beryl (the beryl project merged with compiz). 
 
[Q: Whats the point in hijacking my thread?]("http://ubuntuforums.org/showthread.php?p=3674442#post3674442")

---

### Post by bhencetotozo on 2007-10-30
Ohhh ... it never prompted me to install it.. so what do i do ..

well i think im running 7.10 but ... all i know is that u downloaded it at ubunto website

---

### Post by bhencetotozo on 2007-10-30
Please help me step by step ... :( :(

---

### Post by thelocust on 2007-10-30
Use [envy ]("http://albertomilone.com/nvidia_scripts1.html")to get you drivers. Download the .deb file and install it with Gdebi and then run the envy program. Then you should be good to go.

---

