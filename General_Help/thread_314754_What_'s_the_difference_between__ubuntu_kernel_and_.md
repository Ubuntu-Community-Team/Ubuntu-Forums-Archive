---
title: "What 's the difference between  ubuntu kernel and it's counterpart from kernel.org"
date: 2006-12-08
forum: General Help
---

### Post by jack.ma on 2006-12-08
a

---

### Post by jack.ma on 2006-12-08
What is the difference between ubuntu kernel source geted by "apt-get install linux-source-2.6.12" command and it's counterpart from kernel.org.It is said that the ubuntu kernel developers have done something on the kernel from kernel.org before distributing it.Yes,it is indeed.I met some problems using the kernel from kernel.org on my laptop HP nx6120 although the ubuntu kernel works well.When I reboot the kernel from kernel.org,compiled by myself,it dies at "rebooting" and says "No reboot fixup found for your hardware" in recovery mode.In addition,I find some files in ubuntu kernel source top directory,but not in kernel source from kernel.org,for example Module.symvers,etc..,before or after compiling.

I am a kernel newbie and want to know more.Any suggestion or information is greately appreciately.

-jack

---

### Post by K.Mandla on 2006-12-08
(Merged and moved to General Help. ;) )

---

### Post by Adramelech on 2006-12-08
Kernel from ubuntu is the same as kernel.org but with debian and ubuntu 
patches.

Im not a kernel hacker but i have been reading a little on:
[http://kernelnewbies.org/]("http://kernelnewbies.org/")

not easy at all =)

---

### Post by fragos on 2006-12-08
Compiling the kernel isn't a requirement for most users.  It's an interesting exorsize but serves little measurable purpose unless you have an old slow macine with minimal memory.  There's so much to experiment without do that.

---

