---
title: "MKISS error"
date: 2005-10-31
forum: General Help
---

### Post by cooliohus on 2005-10-31
There seems to be an issue with Ubuntu 5.10 / 2.6.12 kernel that generates the error message below when trying to use kissattach or soundmodem.  News group posts refer to an issue with UDEV and recommend kernel 2.6.14 RC1 or newer.  Are there plans to upgrade the 5.10 kernel (soon)?

TIA, Andy

acooper@leela:~$ sudo kissattach /dev/ttyS0 radio1 44.128.1.1
kissattach: Error setting line discipline: TIOCSETD: No such device
Are you sure you have enabled MKISS support in the kernel
or, if you made it a module, that the module is loaded?

-----------------------------------------------------------------

Newsgroup  	[email]linux-hams@vger.kernel.org[/email]
Subject 	Re: UDEV and MKISS errors with 2.6.12 Gentoo
Time 	Mon 03 Oct 2005 10:11 PM GMT +0800
Sender 	Ralf Baechle DL5RB

On Sun, Oct 02, 2005 at 07:15:38AM -0700, E-mail Protected wrote:  
 
You will need a kernel update to 2.6.14-rc1 or newer.  
 
  Ralf

---

