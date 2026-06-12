---
title: "Unable to run compiz...the output of compiz-check script."
date: 2008-06-04
forum: General Help
---

### Post by scottptn on 2008-06-04
Hello,

Im unable to run compiz on my machine running Ubuntu 8.04 . I ran the compiz-check script downloaded from [http://forlong.blogage.de/article/pages/Compiz-Check]("http://forlong.blogage.de/article/pages/Compiz-Check"). Below is the output of the script.
```


Gathering information about your system...

 Distribution:         **Ubuntu 8.04**
 Desktop environment:  **GNOME**
 Graphics chip:        **VIA Technologies, Inc. Chrome9 HC IGP (rev 01)**
 Driver in use:         **vesa**
 Rendering method:      **AIGLX**

Checking if it's possible to run Compiz on your system...  SKIP

 Checking for hardware/setup problems...           FAIL

There has been (at least) one error detected with your setup:
 Error:Detected driver is not on Compiz' whitelist. 

Would you like to know more? (Y/n) 

```

Any help would be really appreciated 

Thanks :)

---

### Post by hal8000 on 2008-06-04
You need a graphics card thats compatible with opengl support. Looks as though you're out of luck with your Chrome graphic card, as the drive is not on the whitelist :(

Regarding hardware, before I buy anything  I check its on the linux hardware database, Nvidia and ATI actively support linux, so next time you upgrade have a look first at what works well.

---

### Post by scottptn on 2008-06-04
Thanks hal for the reply :) . Well, that has finally put to rest all my doubts . So, ill have to get my graphics card changed to be able to run compiz.

Thanks again.

---

### Post by trevelyan on 2008-06-04
i have your garphics card. and no you dont need to buy a new one to run compiz.
if you read the readme for the instalation driver it says to add via to the whitelist.
that is.. look for your compiz file at /usr/bin and open it with the text editor.
to open it so you can make these changes do copy and paste this in a terminal

sudo nano /usr/bin/compiz

youll see the compiz file contents on the terminal so just look for a line that looks like this (or close to it).

WHITELIST="nvidia intel ati radeon i810 fglrx"

and edit it addin via at the end to make it look like this,

WHITELIST="nvidia intel ati radeon i810 fglrx via"

after that.. press ctrl+X on your keyboard and when it asks if you want to save it just press Y on you keyboard. restart or just press ctrl+alt+backspace and log back in to see if it works now.

another thing... the via driver doesnt work with any kernel above 2.6.24.16
so if you have updated youll have to start on that kernel when you boot.
then everything should work fine.

in case you dont have the driver and were trying to do this with the stock ubuntu driver. you need to download this one.

[http://linux.via.com.tw/support/beginDownload.action?eleid=2&fid=2](http://linux.via.com.tw/support/beginDownload.action?eleid=2&fid=2)

if you need more help.. just let us know. :D

---

### Post by scottptn on 2008-06-04
Hello trevelyan,

Thanks a lot for the reply . I installed the via driver that you pointed out,and also made the change to the compiz file  located at /usr/bin/compiz, 
However, when i rebooted my machine, i got the usual splash screen but the login screen didnt come up. So I pressed ctrl+f1, logged into terminal and uninstalled the driver after which i was back to the previous setup and was able to login.
Anything else that can be done here ?.Also, running uname -r gives the following kernel version : 2.6.24-16-generic

Thanks .

---

### Post by trevelyan on 2008-06-04
after updates and afer you make a change to system files i find that ubuntu does that the first time you reboot.
for me it did that after installing the driver too,  the login screen didnt come up, instead i saw white text on a black background adn it seemed to be doing something.. so i just waited for a little bit and then it showed me the login screen.
maybe you should try again and this time give it a little time to finish reconfiguring.

EDIT:

also.. is your motherboard 4CoreDX90-VSTA  ???
if not does your motherboard contain any of these two chipsets?:
CN896, P4M900

---

### Post by scottptn on 2008-06-05
Hello trevelyan,

Thanks for the reply . My motherboard is not 4CoreDX90-VSTA . But, the chipset model is **Mitac P4M900 Host Bridge**.
Does this have anything to do with the problem im facing ?

Thanks .

---

### Post by trevelyan on 2008-06-05
in that case the driver link i gave you should work for you.. i suggest you try again.. and this time allow time for ubuntu to reconfigure. after a little time it should show you the login screen. also.. make sure you install while running 2.6.24.16
as i remember installing under 2.6.24.17 and then loggend in with 2.6.24.16 and that didnt work. so make the installation under 2.6.24.16
let me know how that goes.

EDIT:
on second thought... whats your motherboard?.. i wanna check compatibility...

---

### Post by scottptn on 2008-06-05
Hello trevelyan,

Thanks for replying. Well, i used a program called Sandra Lite, on Windows to find out my motherboard chipset . Is there any other way i can find out exactly what motherboard im using ?
Im sorry if my question is a bit noobish :)

Thanks for helping me out :)

---

### Post by trevelyan on 2008-06-05
well... you could see if it tells you what it is when you first boot your computer.. you know.. where it says all that stuff about your memory and detected hardrives, etc. it appears breafly but i think you can press the pause/break key to read it. alternatively you could just try installing the driver again.

---

### Post by scottptn on 2008-06-05
Hello trevelyan,

Thanks for the reply . Well, ive noticed that even after waiting for a long time for the login screen to come up, the login screen doesnt come up and all i get is an orange screen with yellow stripes and a bigger than normal mouse cursor.
But, i happened to read the Release Notes of the driver and somewhere at the end it says 


> Default xorg.conf doesn't set display mode in order to let the driver to choose the best one according to the DDC reading of each individual monitor. However, for old monitors that do not have DDC, a Display subsection needs to be added to the xorg.conf file manually to set a mode else it won't display.


My machine is a laptop, so could it be that ill have to set some display mode manually in xorg.conf ?. If yes, then how do i know whats the display mode for my machine and how to add this information to xorg.conf ?

Thanks :).

---

### Post by scottptn on 2008-06-05
Hey trevelyan,

Thanks a million buddy....finally got this thing working :guitar:

The problem was that the driver creates a new xorg.conf which contains the SubSection for "Display" which contains a mode value that doesnt work on my screen. So i set Modes to "1280x800" and Virtual to 1280 800, saved the file and restarted the x-server...and it worked :)


EDIT:
While i was googling for the right mode values for via driver, i came across [http://www.tkarena.com/forums/linux-arena/37154-desktop-effects-amilo-pro-3515-vn896-guide.html]("http://www.tkarena.com/forums/linux-arena/37154-desktop-effects-amilo-pro-3515-vn896-guide.html"), which gives a sample xorg.conf for via.


Thanks a lot for being patient with me and helping me out :)

---

### Post by trevelyan on 2008-06-05
hey.. glad to hear you fixed it... you're right i remember that it sets a default Xorg.
so yeah.. after the install i would get a resolution of 800X600 but that was easily fixed by going to /usr/share/applications  and opening "screens and graphics" and selecting the right kind of monitor and then the resolution it supported.

anyways.. great to know you got it working... now if you like the mac dock you could try avant window navigator. im using it now and it looks nice.. also.. you can install more options to configure compiz by going to system > administration > synaptic package manager  and searching for "compiz" and install compizconfig-settings-manager. it will give you options for the cube desktop and other effects.. its cool.. try it out.:D

---

