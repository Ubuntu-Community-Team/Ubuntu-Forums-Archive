---
title: "Libre Office does not show installed printers."
date: 2017-03-12
forum: General Help
---

### Post by Nailhac on 2017-03-12
I use ubuntu 16.04 with libreofffice 5.3. I have 2 printers attached one via usb and the other via network. Both work well on all software installed on computer apart from libreoffice. No printers are shown other than "generic" and "print to file". I have uninstalled printers and reinstalled them, I have checked my profile but still no success. Any advice would be appreciated.:confused:

---

### Post by DuckHook on 2017-03-13
[LIST=1]
[*]Make and model of printers?
[*]List of apps that do print?
[*]How did you install LibreOffice? Default LibreOffice for 16.04 s/b 5.1.6.2. How did you get 5.3?
[*]Is there anything else non-default about your install? ie custom kernel, added PPAs, apps installed directly from .debs, etc.
[*]Please post output of:```
lpstat -t
``````
uname -a
``````
lsusb
```
[/LIST]
When asking for help, such details are essential, plus whatever else you can think of that is not default.

---

### Post by vasa1 on 2017-03-13
One possibility is that some aspect of OP's profile has gone wonky.

Maybe OP could try renaming *~/.config/libreoffice* to something else after closing LibreOffice completely and making sure that there's no *soffice* process running.

If a restart of LibreOffice doesn't improve things, OP can revert to the original folder name.

Edit: 

This relates to a snap install and so I don't know whether it's relevant: [Snap package: LO doesn't see the printer]("https://bugs.documentfoundation.org/show_bug.cgi?id=105993")

This relates to an older version on Windows: [LibreOffice Writer 4.3.5.2 No default printer found message and can't print.]("https://ask.libreoffice.org/en/question/44022/libreoffice-writer-4352-no-default-printer-found-message-and-cant-print-windows-81/")

---

### Post by DuckHook on 2017-03-13
+1 to vasa1's strategy.

@OP

I have a suspicion that you may have installed by snap since your version is not the default. Is this so?

---

### Post by vasa1 on 2017-03-13
> **DuckHook said:**
> ...
I have a suspicion that you may have installed by snap since your version is not the default. Is this so?
OP may have installed via a ppa. Something like [http://ppa.launchpad.net/libreoffice/ppa/ubuntu?](http://ppa.launchpad.net/libreoffice/ppa/ubuntu?) That would be one route to getting version 5.3.

OP has a thread here: [https://ubuntuforums.org/showthread.php?t=2351605](https://ubuntuforums.org/showthread.php?t=2351605)

---

### Post by DuckHook on 2017-03-13
I ask for that info in my initial reply, but yes. That PPA is how I have installed 5.3. However, I can print.

---

### Post by howefield on 2017-03-13
> **DuckHook said:**
> I have a suspicion that you may have installed by snap since your version is not the default. Is this so?

+1

You can tell if it is the snap version by going to the help menu and selecting "About" - the dialogue box will contain the word snap in the version detail, ie

[ATTACH=CONFIG]274115[/ATTACH]

whereas the deb package will not and look like..

[ATTACH=CONFIG]274116[/ATTACH]

I can confirm the snap package only contains the "Print to file" and "generic printer" options - not picking up the system printers. Not sure how to fix it though, if indeed you can.

---

### Post by vasa1 on 2017-03-13
> **howefield said:**
> ...
I can confirm the snap package only contains the "Print to file" and "generic printer" options - not picking up the system printers. Not sure how to fix it though, if indeed you can.
A bug report is here: [https://bugs.documentfoundation.org/show_bug.cgi?id=105993](https://bugs.documentfoundation.org/show_bug.cgi?id=105993) with this workaround ```
sudo snap connect libreoffice:cups-control :cups-control

The package should enable the cups-control interface automatically.

```

---

### Post by howefield on 2017-03-13
> **vasa1 said:**
> A bug report is here: [https://bugs.documentfoundation.org/show_bug.cgi?id=105993](https://bugs.documentfoundation.org/show_bug.cgi?id=105993) with this workaround 

Thanks vasa1, very cool.

The suggested "fix" works perfectly.

```
sudo snap connect libreoffice:cups-control :cups-control
```

The LibreOffice snap package drops the generic printer and picks up the system printer perfectly.

---

### Post by Nailhac on 2017-03-13
Thanks to DuckHook, vasa1 and howefield for all responses Yes I did install libreoffice by snap . I ran the cups code as you suggested and all works OK. However I had to omit the last " :cups-control" as it was not being accepted as you had suggested. Terminal would only accept "sudo snap connect libreoffice:cups-control"
Many thanks to all who got me up and running.

---

