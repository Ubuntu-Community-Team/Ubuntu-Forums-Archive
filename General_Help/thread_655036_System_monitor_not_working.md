---
title: "System monitor not working"
date: 2007-12-31
forum: General Help
---

### Post by zhimsel on 2007-12-31
Hey guys, for some reason System Monitor closes when I click on the processes tab. All the other tabs work just fine. I can use "ps -e" in the terminal, but it has its limitations.

Anyone else having this problem? I will provide any related system info if needed.

---

### Post by ghostdog74 on 2007-12-31
> **zhimsel said:**
> I can use "ps -e" in the terminal, but it has its limitations.

what limitations ? what is it you want to find ? If you look at the man page of ps, you can see there are lots of options to choose from.

---

### Post by zhimsel on 2007-12-31
> **ghostdog74 said:**
> what limitations ? what is it you want to find ? If you look at the man page of ps, you can see there are lots of options to choose from.

First and foremost: I need to open a terminal... It gets tedious

Second: It doesn't live update. 

Third: It doesn't display CPU usage. This is my primary use for the Process List. To see what app is taking up my CPU.

---

### Post by ghostdog74 on 2007-12-31
> **zhimsel said:**
> First and foremost: I need to open a terminal... It gets tedious

well, you want to use linux, then you have learn to get yourself tedious. :-)

> 
Second: It doesn't live update. 

then the top command might be what you want. It "live updates".

> 
Third: It doesn't display CPU usage. This is my primary use for the Process List. To see what app is taking up my CPU.
Use the top command then. as usual, look up the man page for top for more info

---

### Post by zhimsel on 2007-12-31
> **ghostdog74 said:**
> well, you want to use linux, then you have learn to get yourself tedious. :-)


then the top command might be what you want. It "live updates".


Use the top command then. as usual, look up the man page for top for more info

Thanks a lot! Works great.

---

### Post by zhimsel on 2008-01-01
Is there a similar tool for network usage (or is there a feature in top)? e.g. a tool to list the bandwidth being used by each program?

---

### Post by ghostdog74 on 2008-01-02
I have traffic-collector in my system. You can go [here ]("http://www.mindrot.org/traffic-vis.html")if you want to try it. However, pls also do a search for other similar tools out there.

---

