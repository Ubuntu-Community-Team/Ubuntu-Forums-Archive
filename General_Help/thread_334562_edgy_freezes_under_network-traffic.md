---
title: "edgy freezes under network-traffic"
date: 2007-01-09
forum: General Help
---

### Post by rollli on 2007-01-09
Hi,

On my old faithfull server-workhorse (5years old) I use Linux since 5 years without any problem, from RedHat over SUSE to Dapper 7Month ago, rocksolid. One month ago I changed to Edgy, then the Problems startet. Sooner or later when I have network-traffig the system freezes, independent of the application. I did everything, diabled acpi,apm,agpgart and other common suspects, I used the old Dapper-Kernel, the new feisty, plain Kernels from 2.6.15 to 2.6.20, self compiled and out of the box, nothing helped. I changed my networkcard winbond to 3com, nothing. Becaus it also happend with then dapper-kernel, with that it worked befor I think its not (only) a kernel issue. I suspect the libc6-2.4.1 because it the second core change to dapper after the Kernel. I installed libc6-2.5 from feisty but it stays the same. I

I was so deperate that i tried freeBsd and I m very impressed how reliable, performant and seamless integrated it is, nearly all well known linux-apps or their ports run perfect, dificil things like wifi runs very uncomplicated. The only reason why i not change completely is reiserfs, thats my favorite fs, my apps manage 10-thousands of small files and reiser is best suited for it

Also XP runs ok, so its not a hardware problem

---

