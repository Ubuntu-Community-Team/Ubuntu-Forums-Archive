---
title: "a little problem"
date: 2007-02-02
forum: General Help
---

### Post by nburaq on 2007-02-02
Hi to everyone,
i have an asus a6vm laptop.everything works fine under this laptop! my linux is ubuntu 6.10 edgy.i have problems with my laptop and i need your help pls!
1) wifi works very good under ubuntu however although i close wifi each time,at next startup wifi runs automatically and it disturbs me a lot! how can i disable wireless??

2) although i set lcd's brightness each time i login in ubuntu,at next startup ubuntu forgets the brightness and it sets brightness as maximum level!!! it also disturbs me a lot!!

3) i am still trying to find a driver for my integrated bison webcam!! do you have any suggestion for it?

thanks a lot for your help

---

### Post by x64Jimbo on 2007-02-02
For the wifi, install the NetworkManager application, then comment out the lines about your wifi interface in the /etc/network/interfaces file. Once you've done this, log out and log back in. You can now right click on the Network Manager icon in the task bar and un-check the wireless. 

Not sure about the LCD or webcam. Google?

---

### Post by nburaq on 2007-02-02
thanks a lot buddy,i will try it now and explain the results.this forum really works great

---

### Post by nburaq on 2007-02-02
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp


auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

this is my /etc/network/interfaces result! but i don't know what should i do? can you explain more about the process that i should fallow?

thanks...

---

### Post by jimbob on 2007-02-02
I think he wants you to comment out all but the first two lines pertaining to lo (localhost).

Save the original file first and then make it look like this:

auto lo
iface lo inet loopback

#auto eth0
#face eth0 inet dhcp


#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by mcduck on 2007-02-02
The LCD brightness is set with System/Preferences/Power Management. You can set different defaults for AC power and battery.

---

### Post by nburaq on 2007-02-02
thanks a lot all of your help.now i solved brightness problem :) but i cannot understand the wireless problem? my given data looks like your given data so what is the difference?

thanks....

---

### Post by nburaq on 2007-02-02
ohhh sorry now i understand what you are mentioning about.however should i add eth1 for my wireless connection? do u you have any idea jimbob? like:

auto lo
iface lo inet loopback

#auto eth0
#face eth0 inet dhcp

[B]#auto eth1
**#face eth1 inet dhcp**
[/B]

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

---

### Post by jimbob on 2007-02-02
The pound sign ( # ) in front of all but the first two lines causes them to be treated like comments.

---

### Post by x64Jimbo on 2007-02-02
Follow the instructions given by jimbob. Comment out all the interfaces in your /etc/network/interfaces file that you want NetworkManager to manage - so that's your wifi, and possibly your lan connection if you want it that way. just place the # symbol before any line that you want "commented out." Then follow the rest of the instructions I gave you.
Edit: Beaten!

---

### Post by jimbob on 2007-02-02
No - if you install the network manager as above you do not need any other lines in the /etc/network/interfaces file except the first two.  The network manager will take care of everything - both your wired and wireless connection(s).

---

### Post by nburaq on 2007-02-02
thanks a lot.now it really works.you are great!!!!

---

### Post by nburaq on 2007-02-02
by the way do you have suggestions about what shoul i do for fonts to look nicer on my laptop? installed nvidia drivers with xgl

---

### Post by x64Jimbo on 2007-02-02
You want more fonts? or something like MS ClearType?

---

### Post by klato on 2007-02-02
wow, a lot of people seem to struggle to get their wireless working, and you want to turn if off! ;)

---

