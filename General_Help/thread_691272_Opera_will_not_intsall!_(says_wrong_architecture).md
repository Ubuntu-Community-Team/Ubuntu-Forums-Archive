---
title: "Opera will not intsall! (says wrong architecture?)"
date: 2008-02-08
forum: General Help
---

### Post by UMD TERPS FAN on 2008-02-08
When I try to install Opera its says -Error: Wrong architecture 'i386'  I'm running Ubuntu 7.10 64 bit, on a AMD Turion 64.  Is there a way to get it to install?

Thanks,

Grant

---

### Post by jakommo on 2008-02-08
Hi,

as far as I know opera is not available for 64bit.
As you can see in the error you tried to install the 32bit version of opera.

EDIT:
ok sorry, did a little research an found a solution.

1. you could try the testing version of opera 9.50 which supports 64bit.
go to this site: hxxp://my.opera.com/desktopteam -> scroll down to download UNIX -> x86_64-linux -> opera_9.50-20080131.2-shared-qt_amd64.deb
and install it  

2. you could try to force installation of the 32bit opera .dep
go to the opera download page -> choose "Other/Static dep" under "Select distribution and vendor" -> download it
install it by running 
```
sudo dpkg -i --force-architecture opera-static<version>.deb
```

I hope that helps, I cant test it because I'm at work and we run on i386

jakommo

---

### Post by Khaki Ninja on 2008-04-28
1. you could try the testing version of opera 9.50 which supports 64bit.
go to this site: hxxp://my.opera.com/desktopteam -> scroll down to download UNIX -> x86_64-linux -> opera_9.50-20080131.2-shared-qt_amd64.deb
and install it




Ok, so I was having and i took your advice, and it worked (thanks!)

but i dont see where it installed to.

---

### Post by Khaki Ninja on 2008-04-28
I got it, i just did a simple search and found the aplication. you'll see me around the forums tho, cos im a newb :(

---

