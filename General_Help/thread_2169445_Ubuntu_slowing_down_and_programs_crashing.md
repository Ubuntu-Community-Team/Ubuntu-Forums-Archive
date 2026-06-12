---
title: "Ubuntu slowing down and programs crashing"
date: 2013-08-22
forum: General Help
---

### Post by jason17 on 2013-08-22
Hello All,

I am new to Ubuntu and would really appreciate any help here. 

I am using 13.04, and am having issues with it slowing down, and programs crashing recently. This did not happen before in the past 2 months or so I have been using it.
After being on the computer for about a half-hour or an hour is when this stuff occurs. I have checked system monitor and nothing really stood out other than compiz eating up
like 15 percent of cpu. I also did a "top" from the terminal, and other than one time when program after program was crashing or reporting errors, the only thing to note was apport-gtk I 
think was at like 80 percent. Typically any prog I use when this is going on slows down or is shut down, chrome, gedit, firefox, so I don't think it's particular to any certain program I am
using. My computer is a compaq presario cq61, amd, 4g ram. Thanks in advance for any advice.

---

### Post by erasmusp on 2013-08-22
Hi Jason, except by saying that the programs slow down or shut down, are there any error messages? After a program shuts down can you re-open it again? Also please explain what you mean with "slow down"? Is there any heavy disk activity going on when they slow down?

---

### Post by jason17 on 2013-08-22
The error messages vary. Most commonly is Ubuntu internal error and usually references whatever program I happen to be using at the time when I check the details. Also shows httpd error
sometimes which i think is associated with apache I run. I can usually reopen the programs, but when I do, I experience the same errors. And by slowing down, I mean it's very slow, and there is heavy disk activity going on. It acts as if the cpu is completely bogged down, though when I check, most of the time it is not.

---

### Post by erasmusp on 2013-08-22
My first impression is that this might memory related. It appears that you might be running out of memory and the disk trashing might be the result of memory swapping out to disk, but not very successfully, until it finally crashes. Is this possible? Do you have enough memory available to run all the applications you are trying to? Is there sufficient drive space for the swap area? And, to maybe add on to this, are there not perhaps a bad sector or two in the swap area?

---

### Post by jason17 on 2013-08-23
I don't think it's the memory. I have used 2 different kinds of ram. Errors are the same. Some of the errors read usr/bin/compiz, usr/share/apport - report gtk, and a oserror ('CRC check failed'). Something is really off here, and I can't seem to find the problem.

---

### Post by erasmusp on 2013-08-23
CRC errors point to some hardware failure (or corrupt file) and I still think that this is the area you should be looking at - disk and/or memory. CRC stands for cyclic redundancy check. It is a calculation made from all the data in a file to insure accuracy in transmission. Possible causes include cross linked disk sectors, and mechanical problems with disk drives.

---

### Post by jason17 on 2013-08-23
I think you may be right about the disk. I just hope that's not what it is. The crc error makes sense to me now too. I saw two, I guess you would call them memory values with the not equal to (!=) in between them. I think I will see here soon. I did a reinstall of ubuntu. If problems persist, I think that would definitely point to hardware. However, I'm hoping the reinstall fixed whatever the problem was. I think there is a possiblitly that  something may have been off with apache. Thanks for the help. It is much appreciated.

---

