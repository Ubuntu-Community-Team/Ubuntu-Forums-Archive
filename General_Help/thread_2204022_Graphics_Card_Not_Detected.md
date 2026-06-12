---
title: "Graphics Card Not Detected"
date: 2014-02-06
forum: General Help
---

### Post by duramaxlb7 on 2014-02-06
first post and first-time user of Ubuntu. After about 2 weeks of searching online and trying basically every help guide out there, I finally got my rig to recognize my GPU. I have a Z77 Extreme4 mobo with 2x 2gbxms3 corsair memory sticks and G1620 processor on Ubuntu 12.04 LTS for building a litecoin mining rig. The message I got after installing many iterations of the AMD catalyst driver was 'no device adapter detected'. I installed Beta, 13.11, 13.11 directly and tried fglrx that didn't work. 

The solution was for me to reset the CMOS, update the BIOS to 2.9, run 

'sudo apt-get install update' 

The command that finally worked to completely install the AMD catalyst driver was 

'[COLOR=#4D4D4D][FONT=Open Sans]sudo apt-get install fglrx-updates fglrx-amdcccle-updates fglrx-updates-dev'
 
Next I did something that was probably stupid but worked. I plugged in the GPU with the system on as it was not plugged in when i ran the install command (also probably a mistake). I then used an HDMI cable to plug into one of my monitors. I had been using the DVI-VGA adapter before and that never worked. The graphics card was detected and I ran 

'[/FONT][/COLOR][COLOR=#4D4D4D][FONT=Open Sans]sudo aticonfig --lsa', then '[/FONT][/COLOR][COLOR=#4D4D4D][FONT=Open Sans]sudo aticonfig --adapter=all --initial' then 'sudo reboot'.

I'm not exactly sure what fixed my problems or if it was a combination but this finally worked for me. I can't tell you how many different combinations of things I tried. I suspect that the HDMI, reset CMOS, and different install command is what did it for me. Here is a link to the instructions I followed: [/FONT][/COLOR][http://www.litecoinminingmadeeasy.com/linux-guide.php](http://www.litecoinminingmadeeasy.com/linux-guide.php)

---

