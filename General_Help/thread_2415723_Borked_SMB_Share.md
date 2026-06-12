---
title: "Borked SMB Share"
date: 2019-03-30
forum: General Help
---

### Post by theodorediodorus on 2019-03-30
[FONT=verdana]I am trying to connect to an Ubuntu 16.04 LTS/Linux Mint share through Windows 10 (fresh install, full updates).[/FONT]
[FONT=verdana]I was able to see the Linux share on Windows, enter the /computername and see the shareable folder as well. but when I clicked it, nothing happened. I could hear the drive spin to begin doing work in the other computer, so clearly some signal reached it, but the folder wouldn't open.[/FONT]
[FONT=verdana]Then I googled it trying to fix it myself. Found this [article]("https://social.technet.microsoft.com/Forums/en-US/26e5fd75-f3ab-4ffe-ace4-ed4ba96f82e5/not-discovering-ubuntu-server-on-network?forum=win10itpronetworking"):[/FONT]
[FONT=verdana]where I followed this instruction:[/FONT]
[INDENT]Run Windows PowerShell as 'Administrator'
Enter the following commands:
sc.exe config lanmanworkstation depend= bowser/mrxsmb10/nsi sc.exe config mrxsmb20 start= disabled
reboot
[/INDENT][FONT=verdana]but then I couldn't see the folder anymore.[/FONT]
[FONT=verdana]So I ran what I thought were reverse commands:[/FONT]
[INDENT][INDENT]sc.exe config lanmanworkstation depend= bowser/mrxsmb20/nsi sc.exe config mrxsmb20 start= boot
[/INDENT][/INDENT][FONT=verdana]but now I can't see the Linux machine at all on my computer, and not just a missing folder.[/FONT]
[FONT=verdana]How do I at least get back to square one? Please help! Thanks.[/FONT]

---

### Post by Rubi1200 on 2019-04-01
Hi and welcome to the forums :-)

In an elevated PowerShell:

```
[COLOR=#333333][FONT=&quot]sc.exe config lanmanworkstation depend= bowser/mrxsmb10/mrxsmb20/nsi[/FONT][/COLOR]
```

and

```
[COLOR=#333333][FONT=&quot]sc.exe config mrxsmb20 start= auto[/FONT][/COLOR]
```

Reboot.

First let's see if that gets you back to where you were before trying anything else.

Thanks.

---

