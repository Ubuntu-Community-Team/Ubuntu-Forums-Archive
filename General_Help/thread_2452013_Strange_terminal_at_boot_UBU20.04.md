---
title: "Strange terminal at boot UBU20.04"
date: 2020-10-14
forum: General Help
---

### Post by luxe2 on 2020-10-14
Hi guys I hope you all doing good.


I got alots of problems running ubuntu this past week, getting a bit better every day, but my GPU still acting weird sometimes for no reason. But there still a thing i cant get rid of it.


When i launch Ubuntu at startup, it output me the logger for like 1 second, and just after that, appears a terminal, where i manually have to loggin, and exit, to return to the graphical logger, and re-enter my password. Very annoying thing right here, furthermore i didn't do anything to startup like that. It appear like a terminal 1 , then 2 boot you know what I mean? Is that the secure boot? do you guys have an idea?


Knowing that since i got this terminal at launch, i cant access to my BIOS anymore.


heres my two types of logs after booting,


sometimes this:

[https://ibb.co/4ZGsLj6](https://ibb.co/4ZGsLj6)




sometimes this:

[https://ibb.co/Xk9RPbf](https://ibb.co/Xk9RPbf)


Im running on a MSI Aegis3 8th without any changes.


Im really trying to understand the way that Linux works, am an IT student and I really estimate this OS, despite my lack of knowledges, so if you guys have any informations or advices I will take it.


Thx4support

---

### Post by CelticWarrior on 2020-10-14
Welcome.

> [COLOR=#000000]but my GPU still acting weird sometimes for no reason[/COLOR]
When reporting such issues please always include hardware info and a proper description of the issues.

And before going further please always post any messages or terminal output as code > Click "Go Advanced" for the full editing tools, then pres "#" and paste inside. This preserves format, often fundamental for a correct reading of the problem, improves readability and allows other users to copy/past and search for the problem when trying to help you. In a nutshell, help others help you.

Regarding your problem, "buffer I/O error..." is never a good thing. It can be about logical errors in the said partition - correctable with file system checking tools - or, worse, it may indicate the drive is about to fail.

> [COLOR=#000000]Knowing that since i got this terminal at launch, i cant access to my BIOS anymore.[/COLOR]

One thing has nothing to do with another.

---

