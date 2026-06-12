---
title: "How to deal with the overheat when ubuntu 13.10 is going on?"
date: 2013-10-19
forum: General Help
---

### Post by yumo on 2013-10-19
This is the first time I use ubuntu 13.10,but I have some trouble with.the system always says that it is overheating when I use it for some time.I really want to know how to deal with it!

---

### Post by 3rdalbum on 2013-10-19
1. Check to see if any of the programs are using 100% of the CPU's capacity, which will generate heat, and if this program is not something that you'd expect to use so much (for instance, a video encoder will put your CPU under load, a word processor or file browser will not) then you can try killing it.

2. Even when using 100% of your CPU and 100% of your graphics card capacity, your system should not overheat. Computer hardware is designed to disperse the heat, and in a bad situation it's even designed to go slower so it won't generate so much heat. You should check that the inside of the computer is not choked with dust, that all the computer's fans spin when the computer is turned on, and that you're not blocking any ventilation ports. If your computer's case has a filter, try removing it and cleaning it.

3. If you are still getting the overheating warnings when your computer's insides are clean and the fans are spinning, then your computer is not overheating; it's probably just some faulty sensors, or the software that talks to the thermal sensors doesn't know how to understand what they are saying and thinks that they are reporting very high temperatures.

---

### Post by Linuxisfast on 2013-10-19
If its a hybrid graphic system laptop, install the drivers, either nvidia or amd and also install bumblebee package.

---

