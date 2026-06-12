---
title: "whireshark cann't detect interfaces.."
date: 2008-06-08
forum: General Help
---

### Post by GeNiko on 2008-06-08
Hi,

I installed Wireshark and it starts ok, but cann't find any capture interface ?!? .. any suggestion .. or info ?  

thanks

---

### Post by Monicker on 2008-06-08
You need to start it with root privileges.

ALT + F2
gksudo wireshark

---

### Post by Qwerty_ on 2008-06-08
Ahh I wondered why I couldn't see anything eariler myself.

---

### Post by GeNiko on 2008-06-08
Thanks,  that's it.  When I started it with "gksudo wireshark", dialog appeared "...Running as user "root" and group "root". This could be dangerous...."
-> OK and Whireshark detected and showed interfaces but when I klick start button for capturing, whireshark goes dimmed i.e 'not responding' ... only Force Quit helps ...   

Since I installed Ubuntu yesterday I am new to this OS ... maybe I try to do things like on XP without knowing enough about the OS ... at least I didn't crashed so far ..  :-)

---

### Post by spyder0080 on 2008-07-31
same thing happens to me. I try to capture an interface and the program stops responding. Any help would be appreciated!

---

### Post by GOREMEISTER on 2008-08-14
Same here...

Interface is locked after pressing the "Options" button next to the etho interface.

---

### Post by contactmayankjain on 2008-08-14
same problem here also .. looks like a bug ..

---

### Post by chuky on 2008-08-28
Hi to all
Definitly it seems there is a bug, maybe in gksu(do), maybe in wireshark
puting gksu (or gksudo) in front of the command in the menu enables the interface selection, but upon chosing one, wireshark hangs, not only that, if you run gksu wireshark, or gksudo wireshark in a terminal, same thing happens.
But if you open the root terminal in applications / System, and type wireshark, it runs smoothly. Since is not advisable to leave a root terminal open, type wireshark &, it launch wireshark, and releases the terminal so you can quit it

Carlos Pacheco

---

### Post by air_beagle on 2010-02-19
Hi, Jus downloaded Wireshark from the repositories. Not bringing up any interfaces at all, even though using the sudo command or running it through the terminal.

Running it through terminal gets me this message:
airbeagle@airbeagle-desktop:~$ wireshark
dumpcap: There are no interfaces on which a capture can be done

Im in a cisco ccna class and trying to get wireshark to run to work with it a little bit. Running Karmic Koala and Wireshark 1.2.2. I am not good at checking forums so if you can email me directly at [EMAIL="air_beagle@yahoo.com"]air_beagle@yahoo.com[/EMAIL] that would be very helpful. Thank you very much!

---

### Post by undecim on 2010-02-19
> **chuky said:**
> Hi to all
Definitly it seems there is a bug, maybe in gksu(do), maybe in wireshark
puting gksu (or gksudo) in front of the command in the menu enables the interface selection, but upon chosing one, wireshark hangs, not only that, if you run gksu wireshark, or gksudo wireshark in a terminal, same thing happens.
But if you open the root terminal in applications / System, and type wireshark, it runs smoothly. Since is not advisable to leave a root terminal open, type wireshark &, it launch wireshark, and releases the terminal so you can quit it

Carlos Pacheco

Sounds like it's something to do with environment variables.

---

### Post by air_beagle on 2010-02-19
never mind. changed the startup command for the shortcut that i was using.

---

### Post by willjcroz on 2010-02-21
Hi, no need to run as root! Just use Linux 'capabilities' to add a specific ability to the necessary program...

First, install the packages to get setcap and libcap2. Then set the capability for the dumpcap binary (which wireshark uses to do the raw network capture). As follows:

```
[FONT="Courier New"]sudo apt-get install libcap2 libcap2-bin
sudo setcap cap_net_raw=+ep /usr/bin/dumpcap[/FONT]
```

Next time you run Wireshark as a normal user it should give you full access to all interfaces, and without the security risk of running it as root! :D

---

### Post by james_fried on 2010-10-05
@willjcroz - cheers for this tip. Wireshark was crashing when I was running it with sudo or gksudo

```
sudo setcap cap_net_raw=+ep /usr/bin/dumpcap
```

... got me working straight as normal user!

---

### Post by malkvn on 2010-10-28
I've had a hpmini netbook for a little bit, when i upgraded to 10.10 i thought i'd give getting wireshark to work another crack.  i could never figure out why the wireless wouldn't register in wireshark, it never even occurred to me that it needed root privileges.  I always just assumed it was a driver issue on my crappy wireless card.
THANK YOU!

---

### Post by mickeelm on 2011-11-06
Thank you very much for this! This thread should be marked as solved.

---

### Post by sffvba[e0rt on 2011-11-06
*Back to **sleep** thread...*


404

---

