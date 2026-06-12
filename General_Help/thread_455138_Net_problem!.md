---
title: "Net problem!"
date: 2007-05-26
forum: General Help
---

### Post by shyne_me on 2007-05-26
Hello! this is my first post! I need some help,or some advices. My small hood ISP got bought by a large National company, but before they introduced us a .EXE program which gives net access; and this make`s me sad because i cannot use the Internet in Linux. I am a Ubuntu fan, i have been using it before my ISP gave us that little program. The only link that can i access in ubuntu is tha ine where i can download that program, and nothing else! 

Is there a way that i can make that program work??? or i should talk to the ISP to give me a script or something like that!

---

### Post by dbott67 on 2007-05-26
There should be no reason why you can't use a Mac, Linux or Windows-based PC.  I'm sure the ISP has all the answers.

But, if you can answer a few questions, we may be able to shed some light on the situation.

1. What kind of access do you have: dial-up, DSL, cable?

2. Do you have a home NAT-router?

3. Can you provide any other details as to how your home computer/network is setup?

Thanks,
Dave

---

### Post by shyne_me on 2007-05-26
my connection is ADSL, a 2,5 Mbs line
I don't have a home router, just a switch on the roof of the building
the connection to internet was direct, just put the lan cable in and there you go, until a few weeks ago when they introduced that little program form [www.alcatraz.co.nr](www.alcatraz.co.nr)

---

### Post by dbott67 on 2007-05-26
More than likely, the executable that they're providing is probably some sort of "Net manager" that establishes/configures the PPPoE connection.

In Ubuntu, the program is:
```
sudo pppoeconf
```

You'll need to know your ISP settings & such.

Your best bet is still to contact your ISP.

---

### Post by shyne_me on 2007-05-26
:KS thank you very much I will try it as soon as I partition my HDD! :)

---

