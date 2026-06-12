---
title: "unbuntu antivirus software"
date: 2005-07-02
forum: General Help
---

### Post by Scud89 on 2005-07-02
hi there;
 how are you?

Just wondering if there is any anti-virus software thats worth mentioning as its an essiential peice of utility software although is propberly not the biggest issue on a linux system!

Thanks,
Scud

---

### Post by rachii on 2005-07-02
i never have used any, but i hear a lot about clamAV



here is a very quick and little howto on install and use
[http://ubuntuguide.org/#antivirusserver](http://ubuntuguide.org/#antivirusserver)

---

### Post by Ozitraveller on 2005-07-02
This also available:


F-Prot Antivirus for Linux Workstations - for home users
[http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)

F-Prot Antivirus for Linux Workstations is FREE for use by personal users on personal workstations

---

### Post by Scud89 on 2005-07-02
[QUOTE=Ozitraveller]This also available:


F-Prot Antivirus for Linux Workstations - for home users
[http://www.f-prot.com/products/home_use/linux/](http://www.f-prot.com/products/home_use/linux/)

F-Prot Antivirus for Linux Workstations is FREE for use by personal users on personal workstations[/QUOTE]
 thanks, ill give that a go

also how do i install the .tar.gz file. do i extract it what do i do... im new to linux..

---

### Post by Bandit on 2005-07-03
[QUOTE=Scud89]thanks, ill give that a go

also how do i install the .tar.gz file. do i extract it what do i do... im new to linux..[/QUOTE]

Unless you are worried about spreading windows viruses to other peoples computers then you dont need a antivirus program for linux.
99.9999% of viruses are for windows computers, and they will not harm your linux computer.
Only about 40 viruses where ever created for Linux, and they where created in a Lab.
To the best of my knowledge only 3 were ever released into the public.
You got better chance winning the lottery then you do getting one of those viruses on your machine  ;-) 
Cheers,
Joey

---

### Post by Scud89 on 2005-07-03
[QUOTE=Bandit]Unless you are worried about spreading windows viruses to other peoples computers then you dont need a antivirus program for linux.
99.9999% of viruses are for windows computers, and they will not harm your linux computer.
Only about 40 viruses where ever created for Linux, and they where created in a Lab.
To the best of my knowledge only 3 were ever released into the public.
You got better chance winning the lottery then you do getting one of those viruses on your machine  ;-) 
Cheers,
Joey[/QUOTE]
 kool. your proberly right... thanks for that?

---

### Post by Ozitraveller on 2005-07-03
I have Ubuntu pc's networked into a windows workgroup, I don't want any nasties lurking about my network. Better to be safe than.....!

---

### Post by artinla on 2005-07-03
Scud,

Nothing wrong with having a little added protection.  To answer your question about how to install it, assuming you are running ubuntu:

Download the debian package at:

[http://www.f-prot.com/download/trial_forms/linux-ws-deb.html](http://www.f-prot.com/download/trial_forms/linux-ws-deb.html)

save it to your home folder, then run the following in your terminal:

[COLOR=Blue]sudo dpkg -i fp-linux-ws.deb
[/COLOR]
To scan for viruses:

f-prot /(file or directory to be scanned) 

To update definitions:

sudo /usr/local/f-prot/tools/check-updates.pl


Updates and scans can be automatically done using the linux cron scheduler.  Information can be found at [http://www.f-prot.com/support/unix/unix_faq/index.html](http://www.f-prot.com/support/unix/unix_faq/index.html)


Art

---

### Post by ubunta on 2005-08-09
Hi artinla!

I think is important to have protection  :wink: 

I was trying to follow your instruccions, but when i put 

sudo dpkg -i fp-linux-ws.deb

it begin to run but at the end... processing errors. The problem is that i don't have the libwww-perl. Where can i find it? and how?.

Thanks in advance.

---

