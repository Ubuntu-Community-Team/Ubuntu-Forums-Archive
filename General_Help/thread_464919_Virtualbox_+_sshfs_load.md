---
title: "Virtualbox + sshfs load??"
date: 2007-06-05
forum: General Help
---

### Post by anaconda on 2007-06-05
How much RAM & CPU power would it take to run Dapper in Virtualbox (or VMWare) The only thing I  need from Dapper is sshfs.. 

The Idea is that I would mount some samba shares in dapper and then mount them to feisty  through sshfs. The reason is that Ubuntu Dapper can mount those correctly but feisty or any new linux kernel can't

I am willing to sacrifice some speed to get this working, but how heavy would dapper in virtualbox be? 
I have ADM Athlon 64 X2 Dual Core Processor 3800+

---

### Post by anaconda on 2007-06-07
Works great :)
the CPU load is about 3% when idle, and that is the virtual machine+ubuntu

the only "problem" is that the virtual machine uses too much RAM.. mostly for disk cache. 
Is there any way to turn the disk-cache off?

Oh and I didn't get it working with Virtualbox. VMWare is a lot better in this case. In Virtualbox the vm wasn't visible to other machines and the vm couldn't access other machines.. something to do with Virtualbox NAT settings or something.. In VMWare everything worked from the start!

---

