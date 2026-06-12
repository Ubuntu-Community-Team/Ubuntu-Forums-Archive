---
title: "Understanding Power Saving"
date: 2014-05-31
forum: General Help
---

### Post by linuxyogi on 2014-05-31
Hi,

The best way to save power is most probably shutting down the PC when not in use. 

But problem is if someone feels like returning to the keyboard every 30-45 mins it becomes really troublesome.

I dont know if its true but I have read that the life of a PC (also) depends on the number of boot cycles.

So what is the best way to save power ? Frankly this the first time I am concerned the subject. Our electricity bill is increasing every month and my family is pointing fingers at me ;)

---

### Post by DeMus on 2014-05-31
When you know you will not be using the computer for a longer period of time you can shut it off completely. As you wrote this is the best way to save energy.
But, when you want/have to do something on the computer every 30-45 minutes I would suggest to configure the power settings which can shutdown the hard disk(s), put the monitor in standby mode and put the computer into sleep so the energy consumption will be very little for the in-between-time. Monitor can be switched off manually as well of course, saving even more energy.
Use 5 minutes for monitor and hard disk and maybe 6 for the system before things are put to sleep. This way the system can do all of this before it is put to sleep itself. Play a little with the time settings. Making them too short will interfere with normal work on the computer.

---

### Post by tgalati4 on 2014-05-31
There are different levels of power saving:  

1.  Monitor goes to sleep, but PC is running full speed.
2.  Monitor goes to sleep and PC slows down to slow, idle speed, awake is instantaneous.
3.  PC suspends, CPU stops, RAM has power, disk spins down, and it takes 3 to 8 seconds to awake.
4.  PC hibernates, CPU stops, RAM is written to the swap file (can take several seconds), disk spins down, power remains on the bus, takes 15 to 45 seconds to awake.
5.  PC is shut off through the standard shutdown process.  Power may remain to the bus to power USB devices.  (5 watts or so).
6.  PC is unplugged from the wall.  This is the lowest power option.

How you get to each of these power states depends on your system and which you choose will depend on the annoyance of having to wait for each wake cycle.

There is some wear-and-tear with complete boots versus leaving on 24 hours/day, but the power savings is significant.  What do you pay for electricity?

Check your BIOS for power-saving options.

Some reading:  [https://help.ubuntu.com/community/PowerManagement](https://help.ubuntu.com/community/PowerManagement)

---

### Post by LastDino on 2014-05-31
The only power saving I use is; powering off my monitor as I've more often or not some download etc running. Otherwise, I simply shut the system off. 

This depends largely on persons use, just like how someone running server wont benefit from my way of doing things I wont benefit from his.

Wear and tear from boots hardly matters these days to give it flag up above the power saving done by shutting the system off. 

Other benifit of completely shutting your PC off when you're not doing anything with it is that, it is one of the best ways to protect your system against both hardware damage by power surge and being possible vulnerability. I guess, most advanced countried wont be suffering from former as they use copper wires, but in third world countries, it can happen more often than you can imagin. I've had various components of my PC setup namely: ''UPS (3 Units), Stabilizer(1 unit before buying UPS), PSU (4 Units) and even Mobo (3 Units)'' blown due to same over last 10 or so years.

---

### Post by linuxyogi on 2014-05-31
> **tgalati4 said:**
> 


**3.  PC suspends, CPU stops, RAM has power, disk spins down, and it takes 3 to 8 seconds to awake.**

What do you pay for electricity?

Check your BIOS for power-saving options.

Some reading:  [https://help.ubuntu.com/community/PowerManagement](https://help.ubuntu.com/community/PowerManagement)

That (3) is what I want. Power Management is disabled in Lubuntu so I had to enable it on startup. I have configured it like this :

_ON AC_
Put the computer to sleep when inactive for : 16 mins
Put display to sleep when computer is inactive for 15 mins
Switch off display when computer is inactive for 16 mins

When the computer goes into sleep mode will the CPU stop, disk spins down ?

Our last month's bill was huge. Rs 4000. We dont use a sing AC. A family of 3 paying 4000 is a bit too much here specially with no AC installed. We checked our meter, house wiring for leakage but nothing.


> **LastDino said:**
> The only power saving I use is; powering off my monitor as I've more often or not some download etc running. Otherwise, I simply shut the system off. 

I will have to see if the computer is going to sleep mode when there is download in progress. If that happens I will have to configure the power settings each time I download something but I guess that is unlikely.

---

### Post by LastDino on 2014-05-31
I seriously doubt that your PC is larger contributor to that 4k, I've mine running for around at least 12Hrs per day and our bill comes down to about 1.2 to 1.5k during summers, less when other seasons (around Rs 700 to 800).

---

### Post by Impavidus on 2014-06-01
> **linuxyogi said:**
> 
When the computer goes into sleep mode will the CPU stop, disk spins down ?Yes, they will.
> 
Our last month's bill was huge. Rs 4000. We dont use a sing AC. A family of 3 paying 4000 is a bit too much here specially with no AC installed. We checked our meter, house wiring for leakage but nothing.I've got no idea how much electricity you can buy for Rs 4000 in India. I do know that a desktop computer drawing 100W of power for 10 hours a day will consume 1kWh of energy every day. This would cost me about &#8364;6 a month (US$8, INR480). But as subsidies and taxes vary and you say you're not even on the main AC grid, I can't say what it would be for you.

I can say that a desktop computer can consume op to a few hundred Watts. Laptops, which have smaller screens and more efficient processors, and lack big hungry graphics cards, use far less, with my laptop idling near 12W. On sleeping mode with just the RAM powered, it goes down to 1W. Compare those numbers with the number of hours your computer is switched on and with your electricity rate.

If your energy bill increases every month but your computer usage does not, the computer is not to blame (unless the power supply is failing). There could be some other apparatus in your home causing the trouble. I assume you made sure the door of your refrigerator still closes properly? Those machines can turn into real power drains. It may be best if you can use an electricity meter to check everything in your home, until you find the culprit.

---

### Post by tgalati4 on 2014-06-01
4000 rupees is about $67.60 US.  How much is it per kilowatthour?  In Los Angeles, we pay about $0.14 per kilowatthour.

When your computer goes to sleep, typically the power LED will pulsate slowly, to show that it is indeed asleep.  Put your ear to it and you can hear if the disks are spinning or not when put to sleep.  Measure how many seconds it takes to wake out of sleep.  If only 1 second, then that means the CPU is still running.  If it takes 3 to 8 seconds, then the CPU was halted and modules are being reloaded during the wake cycle and that takes time.

---

### Post by linuxyogi on 2014-06-01
> **tgalati4 said:**
> 4000 rupees is about $67.60 US.  How much is it per kilowatthour?  In Los Angeles, we pay about $0.14 per kilowatthour.

When your computer goes to sleep, typically the power LED will pulsate slowly, to show that it is indeed asleep.  Put your ear to it and you can hear if the disks are spinning or not when put to sleep.  Measure how many seconds it takes to wake out of sleep.  If only 1 second, then that means the CPU is still running.  If it takes 3 to 8 seconds, then the CPU was halted and modules are being reloaded during the wake cycle and that takes time.

The measurements here is done by [units]("http://www.business-standard.com/article/specials/cesc-seeks-18-rise-in-tariff-for-2014-15-114022501317_1.html"). The present rate is Rs 6.71 per unit.

Example 

505 u X Rs 6.71 = 3388 + taxes = Rs 4014.84

The PC is taking about 6 secs to come out of sleep so I guess its working.

---

### Post by Impavidus on 2014-06-01
Rs 6.71=US$ 0.113=€ 0.083. I guess that a unit is about equal to a kilowatthour, maybe with a correction for transmission losses or something like that. I don't think your computer gets anywhere near 505 kWh/month. You have to push it quite hard to get to to 70 kWh/month. There may be another machine to blame. Still, saving power is a good thing.

Interesting though. I pay twice as much for my power as an American and almost three times as much as an Indian.

---

### Post by LastDino on 2014-06-01
> **Impavidus said:**
> Rs 6.71=US$ 0.113=€ 0.083. I guess that a unit is about equal to a kilowatthour, maybe with a correction for transmission losses or something like that. I don't think your computer gets anywhere near 505 kWh/month. You have to push it quite hard to get to to 70 kWh/month. There may be another machine to blame. Still, saving power is a good thing.

Interesting though. I pay twice as much for my power as an American and almost three times as much as an Indian.
This.
Also, better service and safety measures might be the cause here? :p

---

