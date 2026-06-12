---
title: "Running program as root in GUI"
date: 2005-06-08
forum: General Help
---

### Post by michellembrodeur on 2005-06-08
Is there a way to run a program as user root automatically from a gui without first being logged is as root.

thanks

---

### Post by ZeroA4 on 2005-06-08
sudo in a terminal isn't good enough ?

The [Unofficial Ubuntu 5.04 Starter Guide](http://ubuntuguide.org/) has a [How to use "sudo" without prompt for password](http://ubuntuguide.org/#usesudowithoutpasswordprompt) you can use it to make lauchers using sudo program.

[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)

---

### Post by Joeb on 2005-06-08
[QUOTE=michellembrodeur]Is there a way to run a program as user root automatically from a gui without first being logged is as root.

thanks[/QUOTE]

Besides sudo program-name, you can also do a gksudo program-name.

---

### Post by Curlydave on 2005-06-08
"gksudo nautilus" will give you a file browser that lets you change things.

---

### Post by michellembrodeur on 2005-06-08
[QUOTE=ZeroA4]sudo in a terminal isn't good enough ?

The [Unofficial Ubuntu 5.04 Starter Guide](http://ubuntuguide.org/) has a [How to use "sudo" without prompt for password](http://ubuntuguide.org/#usesudowithoutpasswordprompt) you can use it to make lauchers using sudo program.

[http://ubuntuguide.org/#usesudowithoutpasswordprompt](http://ubuntuguide.org/#usesudowithoutpasswordprompt)[/QUOTE]


I asked if it is possible through a GUI, not a terminal prompt!
thanks anyway...

---

### Post by ZeroA4 on 2005-06-08
[QUOTE=michellembrodeur]I asked if it is possible through a GUI, not a terminal prompt!
thanks anyway...[/QUOTE]But if you disable the password prompt it is possible to use the normal sudo from the GUI... that was what I though you wanted...

Sorry i didn't knew about gksudo...

---

