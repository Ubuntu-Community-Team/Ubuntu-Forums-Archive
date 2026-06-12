---
title: "need help with dsl setup"
date: 2006-12-26
forum: General Help
---

### Post by kcampbell26 on 2006-12-26
I'm wondering if anyone can help me with a setup problem.  I recently switched to dsl from dial up and can't seem to get  a connection.  My modem is a generic, but  works fine with WinXP and is also compatable with linux.  The driver disk, of course, only seems to work with windows. I've read a couple of other posts on this forum and the solutions simply don't work.  
The bottom line is that the modem works, but I can't seem to get Linux to recognize it and from there to log onto the network (username and password required) .  Linux still wants to go thru the dial up modem.  Thanks in advance for your concideration.

---

### Post by decideci on 2006-12-26
i also was puzzled in how to get my dsl modem to work.
i just had to run 

> sudo pppoeconf

from a terminal and there i was able to configure my dsl connection. with login and everything. now it connects automatically in the background everytime i startup linux!
that probably should do the trick!

---

### Post by wpshooter on 2006-12-26
If you still have both the dial-up modem and the DSL modem hooked to the machine, the very first thing I would do would be to get the dial-up modem out of/unhooked from the machine and have ONLY the DSL modem hooked to the machine.

Then if your modem works anything like the one that I am using that is provided to me by the Verizon telephone company, you should be able to access the modems configuration program by simply typing it's IP address into your Firefox or other browser and then setting the parameters in the DSL configuration program to the correct settings.  You may want to contact your DSL provider to get assistance with the configuration.  But let me tell you that if yours is like Verizon, you may have to talk to several of their support persons before you can find one that is either **willing** and/or able to assist you with configuring your modem on a Ubuntu/Linux machine.  These people still thing that M/S windows and OSX are the only O/Ss on the planet !!!

Good luck.

---

### Post by kcampbell26 on 2006-12-26
I have typed in pppoeconf, and I get a message that an ethernet card has not been detected.  Then it asks if I want to run modconf, but then refuses to run modconf

---

### Post by baneberry on 2007-01-07
> **kcampbell26 said:**
> I have typed in pppoeconf, and I get a message that an ethernet card has not been detected.  Then it asks if I want to run modconf, but then refuses to run modconf


I have exactly the same problem, but I haven't been able to find a solution.

---

