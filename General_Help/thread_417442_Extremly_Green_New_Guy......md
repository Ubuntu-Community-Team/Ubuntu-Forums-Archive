---
title: "Extremly Green New Guy....."
date: 2007-04-21
forum: General Help
---

### Post by dta116 on 2007-04-21
Needed to download some drivers to fix my wireless adapter. The docs say to create a folder to extract to.

I try to make a folder under /usr but pop up box tells me I do not have privileges to create a folder here.

I am the only logon user on this system. I also cannot extract any files to any folder, I get "cannot extract" errors.

I cannot paste the downloaded .tar files to any directory as there is no paste command after I copied the files.

Where in the world can I change the permissions to configure my system so I can get these tasks done.

I would really like to wipe Windoze from my memory (and computer) but I guess I need more assistance, (book recomendation), than I anticipated.

I first need to get a better grasp of the command line interface (what ever it is called). and what device are loaded when in recovery mode. I plug my USB flash drive in to copy files in recovery mode and errors start scrolling down the screen. It all works when in the Gnome desktop, but cannot copy the files anywhere.

I guess just one step at a time. 

My first order is to get the Video driver to act right, then to get wireless internet. After that things should go much smoother.

---

### Post by taurus on 2007-04-21
Press <Alt>F2 and type 

```
gksudo nautilus
```
Now, you can create a directory in /usr or wherever else you want since you are root now.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by acormack on 2007-04-21
/usr is a system directory and you can't write to it.

create the directory under /home/{username}   

What is the model of wifi card you are using?

---

### Post by dta116 on 2007-04-21
The Wirless Network Card is Intel PRO\Wireless 2195ABG.

I think I have all the files for it but getting them in the right place may be a challenge.

Right now all the files are on the USB Flash drive.

---

### Post by dta116 on 2007-04-21
Tarrus,

I assume the CLI is called SUDO? And these codes must be memorized with much use and a lot of reading to comprehend their meaning?

Can someone please recommend a good Linux Book covering Ubuntu?

---

### Post by acormack on 2007-04-21
Most Intel wireless cards are detected automatically.

If you open a terminal window - select system, konsole

then type 

**iwconfig**

What response do you get?

---

### Post by acormack on 2007-04-21
I just checked and my wifi adaptor is a 

Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)

The model numbers looks very close to yours and it was detected fine in Edgy and Feisty.

---

### Post by dta116 on 2007-04-21
I am showing:

lo    No wireless extensions

eth0    No wireless extensions

eth1    unassosiated ESSID  ~ blah, blah

---

### Post by acormack on 2007-04-22
I am pretty certain now that you don't need to download any files to get your wireless working.

The iwconfig output means that your wireless card (eth1) is detected and working and all you need to do is set up the security settings to connect it to your access point.

There must be some option to do this (unfortunately I use KDE not Gnome so I am not sure exactly what).

Is there an option under Internet or System that allows you to configure your wireless card settings.  Remember eth1 is the system name of your wireless card.

What version of Ubuntu are you running?  If it is not the latest Feisty (7.04) and you haven't got the system running properly yet then it might be worth considering re-installing with Feisty from scratch.

Also did you say you have a  problem with your video display?

---

