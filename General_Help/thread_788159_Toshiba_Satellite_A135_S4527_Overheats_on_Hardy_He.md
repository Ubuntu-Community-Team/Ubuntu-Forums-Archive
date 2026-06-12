---
title: "Toshiba Satellite A135 S4527 Overheats on Hardy Heron?!"
date: 2008-05-09
forum: General Help
---

### Post by Toshibawarrior on 2008-05-09
Ok, so I'm very nervous of getting my laptop (a Toshiba Satellite A135 S4527) roasted. Since I installed Ubuntu Hardy Heron it seems to be overheating more than usual (while I had Vista it overheated, but not so much). And I'm wndering if anyone else is having this problem?

And if there is any way to check if the fan or fans are working on my laptop.

PLEASE HELP!

Thanks in advance!!!

---

### Post by Toshibawarrior on 2008-05-10
bump...
:popcorn::popcorn:
Hello? anyone?? could someone please help me out?

---

### Post by badfish591 on 2008-05-10
i have a toshiba A215-S7428, mine runs ice cold. Windows Vista that came on it ran about 100 times hotter.

---

### Post by tuskpc on 2008-05-10
Have you tried looking at Add to Panel >> and selecting Hardware Sensors Monitor (or) System Monitor?

  I use Ubuntu on a Toshiba, as well as a desktop, and I know the laptop gets hotter than the desktop, but that's normal.  That also might have something to do with ACPI, but I'm not sure though.

---

### Post by Toshibawarrior on 2008-05-11
Thanks for your replies guys! Well on Vista my lappy ran hot...but with hardy it runs kinda the same or even hotter...BUT maaaayyyybe that could be due to the temperatures here where i live...Right now it's like 95 F outside...And when I was running Vista the temp was around 70-80 F. But that's just a thought.

And in reply to tuskpc, yes I tried using Hardware Sensors Monitor and it said "No Sensors Found". And I currently have System Monito running but I don't temperature anywhere.

I was reading about some lm-sensors...but people say it could mess up my hardware, and since my laptop is still under warranty I don't want to mess up anything because of Ubuntu, in case I want Vista to be the culprit so I don't lose my warranty.

Anyways, it's still getting kinda hot. Although I really don't know if it's because th temps outside...or is it just bad configuration.

Anyways, thanks for the replies and any more info or comments will be highly appreciated! :):)

---

### Post by quickwitt on 2008-05-11
I am also on a Toshiba and Ubuntu seems to run hot. You can check the temp by typing this into a terminal 

acpi -V

Mine shows about 60c but the fan always seems to run on high. I think Vista does a better job of power management because the fan throttles down faster.

Looking for any input as to how best to manage the Toshiba acpi.

---

### Post by Toshibawarrior on 2008-05-11
This is what i get when I type acpi -V into terminal...

:~$ acpi -V
     Battery 1: charging, 90%, charging at zero rate - will never fully charge.
No support for device type: thermal
  AC Adapter 1: on-line

So I guess I'm screwed about thermal thingies...:(:confused:

Any help is still highly appreciated...!

---

### Post by Toshibawarrior on 2008-07-10
BUMP...Still need help on this!

---

### Post by PeterWalgreens on 2008-08-17
I never used this machine for vista, but my A135 runs like a toaster oven. On fire. It randomly shuts off, but given the relative age, quality, and price (400 dollars) of the machine, I gotta say, I've gotten my money back, seeing it runs almost 24/7 in a dirty inviroment, and is my ''daily beater''. My advice? Make sure the bottom fan is free. The side fan is nearly useless, but as long as the bottom area of the compuer isnt restricted, the computer will cool off fast.

---

### Post by plb on 2008-08-20
Try turning CPU Scaling from dynamic to always low in the bios

---

### Post by Toshibawarrior on 2008-11-17
Problem solved in Intrepid Ibex!

---

