---
title: "Copying a .dat file in kubuntu?"
date: 2007-05-30
forum: General Help
---

### Post by true_friend on 2007-05-30
Hi folks have a problem from a long long time. I've never been able to copy a .dat file form CD-ROM through ubuntu(kubuntu) it is clarified that cds were always well and worked through windows same thing i.e. copy of .dat files( i have dual boot kubuntu + windows) so can some one help me???????

---

### Post by eyelessfade on 2007-06-01
a *.dat? isn't that just any other binary file? should be no problem to just mount up the cd and cp /path/to/cd/mine.dat /home/username/ etc

---

### Post by true_friend on 2007-06-21
It is just a movie file on a cd. can say a vcd. but I never be able to copy such file in kubuntu.

---

### Post by Qu4k3R on 2007-06-21
Have you tried to move the file with the Konsole ?

You should move it to your hdd then use it then as you would wish.. 
Use the "cp" command to copy it.

:D

---

### Post by manmath on 2007-11-26
oh my god! dear forum members please remember that anybody who asks for a solution on "how to copy vcd" definitely knows how to copy a file off a cd to hdd on x and on console. so, don't teach how to teach copy a file on linux.

however, the issue is, it is difficult to copy a vcd in linux. it's not like other cdroms. to copy a vcd one has to install cdfs modules. after cdfs installation one can issue "mount -t cdfs /dev/cdrom /mnt/xyz" to be able to browse the mpeg files in that vcd.

otherwise one can install vcdimager and issue "vcdxrip" to rip mpeg files from a vcd. one can also use mencoder to rip off a dvd onto hdd.

so, the bottomline is you can't copy vcds onto hdd the way you do with other cdroms.

hope it makes enough sense.

---

