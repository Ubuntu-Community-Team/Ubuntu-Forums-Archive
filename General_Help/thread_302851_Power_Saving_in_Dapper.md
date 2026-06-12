---
title: "Power Saving in Dapper"
date: 2006-11-19
forum: General Help
---

### Post by wiz561 on 2006-11-19
Hi!

   I'm running the 2.6.15-27-amd64-k8 kernel on 6.06 LTS.  I have a MSI motherboard with an AMD64x2 chip.  I use this box for mythtv and would love to try to start saving power.
  
   I'm trying to figure out acpi-tools and acpid, but don't quite know what I'm doing.  My whole goal is to start saving energy.  I don't really see a need for me to leave my box on full power overnight, or when I'm not using myth.  I found this page...

[http://www.columbia.edu/~ariel/acpi/acpi_howto.txt](http://www.columbia.edu/~ariel/acpi/acpi_howto.txt)

   but somehow have a feeling that it's outdated since it talks about the 2.2 kernel.  I also saw some other packages available, like powersaved, but don't know what the best route to take is.

   The most important thing is that I don't want to fry my processor from a cpufan going off.  After that, I would love to be able to put my machine in sleep mode that will wake up if a myth recording is scheduled, or if I press the power button on the myth remote.  Third of all, I don't know if I'm living in a dreamworld or not, but if I would like to use this box as a webserver, could I have the box wake up if somebody tries to visit the web site or ssh into the box?

Thanks for any help!!!

---

### Post by superm1 on 2006-11-19
Is this box a frontend or a backend box?  If its a master backend, i wouldn't be shutting it off...

---

### Post by wiz561 on 2006-11-19
Actually, it's both.  :-)  

Is there a reason why you don't recommend shutting the backend off?   I was reading some of the myth docs, and if it's about missing a recording if the cpu shuts down, myth can control this.  You can setup myth so that it adds a startup time to  /proc/acpi/alarm  file.  When a time is added, the machine automagically turns on and starts recording the program.


Thanks!

---

