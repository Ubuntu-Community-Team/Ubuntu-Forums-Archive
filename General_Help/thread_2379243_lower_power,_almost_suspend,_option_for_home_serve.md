---
title: "lower power, almost suspend, option for home server?"
date: 2017-12-02
forum: General Help
---

### Post by derekcentrico on 2017-12-02
Howdy.  So, my home server is running all the time (24/7) and makes quite a bit of heat.  I'd like to limit its operation to when in use.  

I tried suspend wakeonlan but was kind of in a hard spot because my Eero router doesn't support the waking packets I guess.  

I have hard drives going to power down mode after 15 minutes of inactivity.  However, still lots of heat is generated because the machine is still operational aside from the 5 hard drives.

What else can I do to go into lower power mode until the system is needed?

Home server is used for backup and media streaming.  I am not always home, so the remote necessity for access kills the wakeonlan option...

Thanks for any input possible.

---

### Post by vasa1 on 2017-12-02
Did you accidentally mark your thread [SOLVED]? If so, see [How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by derekcentrico on 2017-12-02
My bad thought I flagged Ubuntu and not solved. 

Help needed.

---

### Post by QIII on 2017-12-02
Hello!

Do you have the CPU overclocked?  Do you have power stepping enabled in your BIOS?  Does your server have a GPU?  Is it overclocked?  Have you installed lm-sensors or psensor to monitor your temps and see what is high?

---

### Post by derekcentrico on 2017-12-03
Thanks for jumping in!

Quick point of clarification... the system isn't running hotter than I would expect but the fact that it's running 24x7 really adds a lot of heat to the room and burns power unnecessarily.

No overclocking. Totally ignorant to power stepping so I'd guess no.

It has a gpu installed and I use it rarely. not overclocked either.

I do have sensors installed. Hard drives run 90 to 110F. CPU runs 95 to 115F load dependent.

Advise appreciated.

---

### Post by QIII on 2017-12-03
Those temperatures are pretty much expected at idle.  Your body is about that warm. I suspect that you are drawing < 175W at the wall at idle even if you are using a very powerful processor and GPU.  A lot less if using more modest equipment. Less heat than the output of two 100W incandescent light bulbs.  And given the typical efficiency of a normal PSU,  just having that running is a significant component of the heat being generated.  That is about as low as you are likely to go.  There's not much we can do about physics.  The only other options would be to shut down or hibernate with WOL to bring it back up.

You could always turn off a couple of lights.  

You, by the way, produce about 100W while sitting on the couch.  If you have someone living with you, your combined idle wattage is likely more than your server at idle.

---

### Post by derekcentrico on 2017-12-03
I understand but the best output truly increases the temperature of the room and is a wife complaining point.

I considered WoL but it appears that it won't wake from WAN requests. Or, is there a modification so that a LAN magic packet is not needed?

---

### Post by dragonfly41 on 2017-12-03
Musing here ...
Would a connected Raspberry Pi between router and server work?

[https://www.raspberrypi.org/documentation/remote-access/access-over-Internet/](https://www.raspberrypi.org/documentation/remote-access/access-over-Internet/)

Power consumption ...

[https://www.pidramble.com/wiki/benchmarks/power-consumption](https://www.pidramble.com/wiki/benchmarks/power-consumption)

---

### Post by derekcentrico on 2017-12-03
Interesting thought.  It would be cool if it could send a WoL of some sort without being in between the network and the server.  Reason being two gigabit NICs on USB is something I never trust.  Remote connection gigabit is irrelevant, but internally my nerdy game streaming could be affected when other server actions are ongoing.

---

### Post by dragonfly41 on 2017-12-04
Found this tutorial from simple search ...

[http://www.instructables.com/id/Raspberry-Pi-As-Wake-on-LAN-Server/](http://www.instructables.com/id/Raspberry-Pi-As-Wake-on-LAN-Server/)

---

