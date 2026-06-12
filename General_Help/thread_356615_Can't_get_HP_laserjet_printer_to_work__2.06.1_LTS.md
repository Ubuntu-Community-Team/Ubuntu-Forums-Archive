---
title: "Can't get HP laserjet printer to work  2.06.1 LTS"
date: 2007-02-08
forum: General Help
---

### Post by Jensor on 2007-02-08
I am trying to get my printer to work in ubuntu 6.06.1 LTS with kernal 2.6.15-magma.


After going through System-Administration-Printers and adding HP Laserjet 4P, it looked for HP-Laserjet_4P-hpijs.ppd and apparently installed it. 

To check to see if it worked, I went to System-Help and from the file menu selected print this page. Then a window came up with 3 offerings - Create a PDF document, Generic Postscript, and Laserjet-4P. I selected my printer (Laserjet-4P) and clicked on print. It looked like it accepted this, however the printer stayed dormant.

I then selected System-Administration-Printing and a window comes up and I right clicked on my HP Laserjet 4P and selected jobs from the drop down list and then got another window which indicates that job 1 is printing. Printer is still dormant.

Any ideas on how to fix this?

I need to mention that my Linux machine is not on the internet. The only way I can access and down load any files is through another PC on Windows XP and transfer the files to the Linux machine via a flash memory stick. I have already learned the hardway that Ubuntu assumes you have an internet connection. Then bombs out if you don't. I'm in the process of getting an external modem to get past that problem.

Jack Ensor

---

### Post by Sef on 2007-02-08
Did you click Forward and not install when you got to that window?

---

### Post by Jensor on 2007-02-09
> **Sef said:**
> Did you click Forward and not install when you got to that window?

Yes, I went through found file in /usr/share/ppd/custom and installed the specified file and got a new pinter icon "Laserjet-4P" ready in the window.

I tried removing the printer and reinstalling and when I went through the re-install process I got an error saying that the file was already installed. I clicked okay and went on thru. still get same result the printer icon says printing 1 job, but the printer is inert.
Jack Ensor

---

