---
title: "Unable to turn cooling devices on"
date: 2007-02-14
forum: General Help
---

### Post by warri0r on 2007-02-14
oooooops i think i m with some serious issue. since i installed ubuntu i m getting an error flooded in all my system logs and even at the time of booting.

the error is "**unable to start cooling devices on**" :(

wat i need to do and my cpu temperature is** 68* c** :(  (got this via command **acpi -t**)

i m know my cpu ll go crazy soon :(

plz someone help.

---

### Post by hardyn on 2007-02-14
please post hardware specs!

i know there has been trouble on dual core dells with early bios, and intel apples.
but for anybody to help we are going to need more info!

thanks.

---

### Post by warri0r on 2007-02-14
sorry here the specifications tat i know

AMD Athlon XP 2000 Mhz
Via chipset
nVidia geforce FX5200
Linksys WMP54G wireless lan card (Ralink rt61 chipset)
1.25 GB DDR ram

this is all i know, if u need anything else plz tell me how to obtain them as i m damn newbie to linux :(

plz help dude

---

### Post by hardyn on 2007-02-14
is this a notebook or a desktop?

---

### Post by warri0r on 2007-02-14
Absolutely a desktop

---

### Post by warri0r on 2007-02-14
here are some screenshots of various log files :( 

[[IMG]http://img513.imageshack.us/img513/6055/screenshot1cd6.th.png[/IMG]](http://img513.imageshack.us/my.php?image=screenshot1cd6.png)


[[IMG]http://img503.imageshack.us/img503/8969/screenshot2jk9.th.png[/IMG]](http://img503.imageshack.us/my.php?image=screenshot2jk9.png)

[[IMG]http://img513.imageshack.us/img513/2111/screenshot3qw1.th.png[/IMG]](http://img513.imageshack.us/my.php?image=screenshot3qw1.png)


hope it may help

---

### Post by hardyn on 2007-02-14
somebody can correct me if i am wrong, but most chipsets of that vintage did not provide "smart fan" and the pulled a full 12v off the motherboard at all times. speed control was just something that they didn't have.

im not even sure if a motherboard of that vintage is even capable acpi? its something that you might want to check. or it may have been provided as bios update, if acpi is not enabled on that motherboard, disable acpi support in grup with a boot string and the errors will go away. 

If you specific vendor did provide some smart fan capability it may have been done with windows specific drivers, or some other non standard that linux (written quite rigidly to spec) may not have the ability to control, there may be vendor specific kernel patches to fix this.

is the CPU fan not turning at all?  if the cpu is turning, im betting its turning at full speed and their is really nothing to worry about and ingore the errors becuase acpi is trying to find something that isn't there.  if it not turning then their are a couple of options.

1) find somebody with more knowlege about your specific setup for linux.
2) use a case fan 12v output on the motherboard
3) get one of those disk drive molex connector fans.

i did an identical system this xmas from mom, it was a AMD XP2400 with asrock socket A motherboard.  it did have limited acpi support for suspend and hybernate, but did NOT have variable fan speed support, and that is just the way it is.  fan speed is a function of fan design, or by inline resistance, is what i did, soldered a resistor inline to reduce fan speed from 5000rpm to 3200rpm... still cools just fine, but doesnt sound like a jet.

let me know how it goes for you.


1

---

### Post by warri0r on 2007-02-14
searched on google and got this

[https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63550](https://launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/63550)


i hope i dont hav any problem with my fan as i made a test last night with windows

i kept the cabinet opened and tested whether its running r not when i m on windows, well it does smart at some intervals.

then i switched to linux this morning and till now i havnt seen tat running , it keeps idle :(

i dont know any hardware screwing as i m relly weird abt it 

this system keeps running 24/7 tats y i m worried a lot.

plz help wat can i do and i m really screwed since i switched to linux and seriously thinking abt returning to windows :(

---

### Post by warri0r on 2007-02-14
got the output for the below command 

cat /proc/acpi/thermal_zone/*/*

cooling mode:   active
<polling disabled>
state:                   passive 
temperature:             66 C
critical (S5):           100 C
passive:                 -248 C: tc1=4 tc2=3 tsp=60 devices=0xdffed338 
active[0]:               -266 C: devices=0xdffeddec 

someone help plz

---

### Post by hardyn on 2007-02-14
i know that this isn't the best solution... but...
unless that motherboard is really special, and if you don't mind spending a little bit of money, a socket A motherboard can be purchased for about 40$ new.

something to think about.  might be easer that trying to fight with kernel incompatibility.

---

