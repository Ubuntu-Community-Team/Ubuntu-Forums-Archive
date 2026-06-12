---
title: "Broken package manager"
date: 2007-10-20
forum: General Help
---

### Post by k420 on 2007-10-20
I tried to install the drivers for my printer at work.  mfc9700lpr now i can not us apt-get or aptitude.  It keeps telling me to run sudo apt-get install -f but it does not work.  any idea how to remove this file so my package manager will work

---

### Post by bapoumba on 2007-10-20
Could you please post the complete error message?

---

### Post by k420 on 2007-10-20
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been automatically kept back:
  gnucash-common
The following packages have been kept back:
  gnucash
The following packages will be upgraded:
  hpijs hplip hplip-data kompozer libmysqlclient15off mysql-common tk8.4 tzdata wine
9 packages upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0B of archives. After unpacking 1012kB will be freed.
Do you want to continue? [Y/n/?] y
E: I wasn't able to locate file for the mfc9700lpr package. This might mean you need to manually fix this package.
E: Couldn't lock list directory..are you root?
nathan@nathan-laptop:~$



and i used sudo aptitude upgrade

---

### Post by bapoumba on 2007-10-20
Hmm, google does not say anything about this error. How did you install the package?

---

### Post by k420 on 2007-10-21
I manually compiled the package from the brother website ( manufacturer of the printer)

---

### Post by k420 on 2007-10-25
any help please

---

### Post by bapoumba on 2007-10-25
Sorry..
Are there removal instructions in a readme file from the package you dowloaded ?

---

### Post by k420 on 2007-11-01
no there were no uninstall instructions with the package
here is the link to where i got the file [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")

---

### Post by Maestro23 on 2007-11-01
> **k420 said:**
> no there were no uninstall instructions with the package
here is the link to where i got the file [http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html]("http://solutions.brother.com/linux/sol/printer/linux/lpr_drivers.html")

Exactly which one did you download?

---

### Post by k420 on 2007-11-01
mfc-9700

---

