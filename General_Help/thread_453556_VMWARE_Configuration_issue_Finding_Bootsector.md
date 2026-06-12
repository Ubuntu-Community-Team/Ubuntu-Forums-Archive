---
title: "VMWARE Configuration issue: Finding Bootsector"
date: 2007-05-24
forum: General Help
---

### Post by aram_mm on 2007-05-24
Hello everyone. 

After trying Ubuntu, Kubuntu and Xubuntu, I have kept the last one while I learn more about linux in general and decide which one I actually want to use. So far everything has been just as (not) easy as expected and I can currently do almost anything I want with Xubuntu. Unfortunately, there is one damned Windows application that I want to use and Wine does not cut it this time. 

I have been following this:

[http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html](http://www.advicesource.org/ubuntu/Run_Existing_Windows_Instalation_On_Ubuntu_With_Vmware_player.html)

and this:

[http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

When I get to the point when I have to copy the bootsector, I just cannot find it. This is what I get:

-@laptop:~$ sudo dd if=/dev/hda of=WindowsXP.mbr bs=512 count=63
dd: abriendo `/dev/hda': No existe el fichero ó directorio  (that means pretty much, "/dev/hda does not exist")

I created the / hda folder in dev, then created a document, but it did not help. 

I wonder if I should change /hda for /sda, as I get a gut feeling that that is the solution, but I would rather ask, instead of letting my guts rule over my system.

Am I right? Any other suggestion?

Thank you.

(btw I am not a native speaker, sorry if I have not explained myself clearly enough).

______________________________________________________________________________________________________

POST EDITION:

My guts were right. I just had to replace hda with sda. Just in case anyone has the same problem.

---

