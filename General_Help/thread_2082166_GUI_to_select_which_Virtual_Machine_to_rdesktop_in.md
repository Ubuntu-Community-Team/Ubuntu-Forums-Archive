---
title: "GUI to select which Virtual Machine to rdesktop into"
date: 2012-11-08
forum: General Help
---

### Post by greavette on 2012-11-08
Hello,

We use Virtual Machines as Desktops in our small office.  We have at our workstations small fanless PC's with Ubuntu Desktop Installed.  I'd like to have it where each Ubuntu Desktop has on it a GUI that lets our users select the Virtual Machine assigned to them to rdesktop into.  I know I could use shortcuts for each VM, or TSclient, but I was hoping for something where the user just selects the VM (Radio Button beside the VM name for example) and click OK to start the rdesktop session.  Maybe using a bash script and putting a GUI in front of it (like I would with Powershell or Autohotkey on Windows).  

Any ideas on what I could use would be greatly appreciated.

Thank you.

---

### Post by Habitual on 2012-11-08
[something I wrote]("http://www.bournetoraiseshell.com/article.php/20110702095228930") some time ago as a "GUI" / FrontEnd to handle multiple ssh connections using ssh-keys.
This could be reworked into your intended script with some modifications.

Requires zenity (or could be yad too) 
and some script.fu, do you code at all?

---

### Post by greavette on 2012-11-08
Thanks very much for bringing these tools to my attention. 

I think this is exactly what I need. 

Thank you.

---

### Post by dcstar on 2012-11-09
> **greavette said:**
> Hello,

We use Virtual Machines as Desktops in our small office.  We have at our workstations small fanless PC's with Ubuntu Desktop Installed.  I'd like to have it where each Ubuntu Desktop has on it a GUI that lets our users select the Virtual Machine assigned to them to rdesktop into. 
...........
Any ideas on what I could use would be greatly appreciated.


You simply give each user their own login account and a simple Desktop shortcut that is customised for that user.

There is no need whatsoever to over-complicate this simple requirement.

---

### Post by Habitual on 2012-11-10
> **greavette said:**
> Thanks very much for bringing these tools to my attention. 

I think this is exactly what I need. 

Thank you.

David/dcstar is correct. It may be over doing it somewhat.

> **greavette said:**
> users select the Virtual Machine assigned to them If it assigned then why allow choice at all?


JJ

---

