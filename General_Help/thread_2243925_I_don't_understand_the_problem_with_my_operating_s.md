---
title: "I don't understand the problem with my operating system.."
date: 2014-09-12
forum: General Help
---

### Post by ollylove on 2014-09-12
hello everybody!!..
I'm going to explain you the problem with my computer, an annoying problem which affects my computer, but I don't understand what it is!!..

I bought a new laptop (with both hard disk and SSD) in july and I installed kubuntu 14.04 lts (with two partitions: filesystems on the SSD and home on the hard disk)..
everything went fine, I installed pulseaudio-equalizer for improving the audio and everything was fine and great.. but one day, about a month ago, I read about pavucontrol and qpaeq, a better equalizer, and I wanted to try it.. I installed both programs, but they never worked, rather: the audio didn't work anymore, in audio settings I could see only HDMI option and nothing else.. since I found no solutions on the internet, I reinstalled kubuntu.. but I didn't format the partitions, so the system didn't work and the sound still didn't work.. I reinstalled kubuntu formatting the already existing partitions, and the system seemed to be working.. but when I rebooted, kubuntu stopped at boot, leaving black screen and the only thing I could do was ctrl+alt+f1, log in and type "startx".. this was the only way for the system to launch the desktop.. but nothing worked, nor the audio (dummy output), nor openGL, nor some programs.. I thought, probably formatting the single partitions wasn't enough, I should format the entire system.. so I did it: I cleared the entire system, hdd and ssd, and reinstalled kubuntu once again.. that seemed to be the working solution, the audio worked perfectly, all the graphical effects worked (openGL), everything!!.. I rebooted the system several times (after every time I changed some settings) and every time everything went great.. till the last time: I only set the system to turn on the numlock at boot and installed a new pointer; I rebooted and again kubuntu stopped at boot leaving black screen.. after logging in with the command startx, again neither the audio (dummy output), nor openGL work.. and I don't understand, I didn't install pavucontrol or qpaeq or other **** and I don't understaaaaaaand!!..
do you think the problem is hardware??.. then why does the system work for a period and then gets broken??..

if it helps, here you can see the messages after I turn off the computer or log out my account:

[https://drive.google.com/file/d/0B3yxZDKAwTB6cHJ5M0JEUkZJSlU/edit?usp=sharing](https://drive.google.com/file/d/0B3yxZDKAwTB6cHJ5M0JEUkZJSlU/edit?usp=sharing)

can anyone help me??.. I really don't know what to do..
thank you so much!!..

---

### Post by ollylove on 2014-09-13
hello??..

---

### Post by pissedoffdude on 2014-09-13
Hi,

Can you be specific on what 'settings' you changed that resulted in an error upon reboot (which program you installed/used and the features you enabled in that program)?  Also, be sure to post your system specs or computer model.

---

### Post by ollylove on 2014-09-14
[FONT=arial]nothing special, settings for the power behaviors, color schemas, pointer themes and thing like that.. I also installed chrome and chromium, but I don't think they make a problem..
my computer is a MSI [COLOR=#000000]GS70 2PC Stealth; intel [/COLOR][/FONT][COLOR=#000000][FONT=Arial] i7-4710HQ; 16gb ram; [/FONT][/COLOR][COLOR=#000000][FONT=Arial]NVIDIA GeForce GTX 860M, 2gb[/FONT][/COLOR]

---

### Post by ian-weisser on 2014-09-14
> **ollylove said:**
> every time everything went great.. till the last time: I only set the system to turn on the numlock at boot and installed a new pointer

What does "installed a new pointer" mean?
What exactly did you install and how?

Also, try booting from a live USB and run fsck on your unmounted system disk to rule out some types of hardware failure.

---

### Post by ollylove on 2014-09-15
sorry, I badly explained.. I installed a new pointer theme.. I followed this guide: [http://goo.gl/INdfjh](http://goo.gl/INdfjh)
but I finally understood the problem, and I can't believe it was that very pointer theme!!.. after I followed the guide and rebooted, again the system didn't start.. but removing the theme from the konsole and rebooting it worked again..
but I'm confused, why did it work the first time I installed kubuntu??.. :-s
now it's asking me for updates.. do you think after updating the system something could go wrong??.. I'm a little bit hesitating..

---

### Post by Bucky Ball on 2014-09-15
Update the system. You need to eventually. It might actually fix some things.

---

### Post by ollylove on 2014-09-15
you're right.. ok, I just did the updates and everything is working and fine..
can I just ask you quickly, do you know if there's a ppa to add to my kubuntu in order to keep the KERNEL updated??..
many thanks!!..

---

### Post by marco-parillo on 2014-09-15
> **ollylove said:**
> you're right.. ok, I just did the updates and everything is working and fine..
can I just ask you quickly, do you know if there's a ppa to add to my kubuntu in order to keep the KERNEL updated??..
many thanks!!..

If you regularly apply updates (the easy and default way is to get an indicator in your panel, and click on it to launch Muon Update Manager), you will get updated Kernels.

---

### Post by ollylove on 2014-09-15
ok, thank you so much!!..
bye friends!!.. ;-)

---

