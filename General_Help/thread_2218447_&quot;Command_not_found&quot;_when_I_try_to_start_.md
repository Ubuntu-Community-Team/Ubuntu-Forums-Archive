---
title: "&quot;Command not found&quot; when I try to start a program or script"
date: 2014-04-20
forum: General Help
---

### Post by bitencrypt on 2014-04-20
Ubuntu 12.04.2, x64, Gnome.

CNF = "Command Not Found"

I type sudo lsb-release -a "CNF", sudo /opt/lampp/lampp start "CNF". 

I think it has to do with nautilus itself because, I forgot to use >>>gksudo<<< nautilus. Then CNF started showing up.
I have looked at the file chown and chmod. It all looks good.
 
I dont know what to do to get it back to working again.

---

### Post by grahammechanical on 2014-04-20
[COLOR=#000000] "CNF"

Why are you including that as part of the command? I can run lsb_release -a without the need for sudo. And I get this

[/COLOR]> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

But if I replace the underscore with a hyphen as you have done, I get this

> No command 'lsb-release' found, did you mean:
 Command 'lsb_release' from package 'lsb-release' (main)
lsb-release: command not found


Regards.

---

