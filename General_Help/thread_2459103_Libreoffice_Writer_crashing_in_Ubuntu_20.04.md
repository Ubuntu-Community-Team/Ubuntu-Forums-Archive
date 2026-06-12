---
title: "Libreoffice Writer crashing in Ubuntu 20.04"
date: 2021-03-10
forum: General Help
---

### Post by Tupaq on 2021-03-10
I'm sorry if this was posted elsewhere, but I searched the forums and DuckDuckGo and couldn't find anyone else having this issue. I have been consistently having LibreOffice Writer crash randomly when saving in Ubuntu 20.04. Shutting down and rebooting does nothing, as this problem has been going on consistently for quite a while. Normally, I can save my documents without issue, but sometimes the programme and the entire desktop freezes when I try to save my document. I end up needing to recover my document after my computer has stopped being frozen. Curiously, it appears that Writer nonetheless saves the data the time it crashes. I don't regularly use other parts of the LibreOffice suite, so I am unsure as to if this would be a problem in Calc or Impress.

I am running Ubuntu 20.04 on a rather old Dell Inspiron-15 3521. The version of writer I have is apparently: 1:6.4.6-0ubuntu0.20.04.1 .

I will be submitting a bug report soon to hopefully help others who may have this problem.

Thank you for your help!

---

### Post by CelticWarrior on 2021-03-10
Can you read/write to other files in the same location where you're trying to save?
Please hold on the bug report as this very likely has to do with the problems in the drive rather than a bug in Writer.

---

### Post by Tupaq on 2021-03-10
> Can you read/write to other files in the same location where you're trying to save?

I'm sorry, but what do you mean by "read/write to other files in the same location"? I'm not sure what you're asking me to do or try. Thank you

> Please hold on the bug report as this very likely has to do with the problems in the drive rather than a bug in Writer.

Okay I'll do that then.

---

### Post by CelticWarrior on 2021-03-10
In the same location - folder/partition/drive - where you're trying to save the Writer's files do you also experiment problems when reading and/or writing other files?

---

### Post by Tupaq on 2021-03-10
Okay then I think I understand. I have had issues only on my desktop, where I also only have writer (.odt) files on my desktop. No crashes have occurred from opening .odt files elsewhere, such as in the "documents" or "downloads" folders accessed through the file manager.

EDIT: I have never had problems with .pdf files or other files such as .odp files, if that helps.

---

### Post by grahammechanical on 2021-03-10
How much memory (RAM) does that rather old Dell Inspiron have?

I used to run Ubuntu and Libreoffice quite well with 1 GB RAM. Then I started editing two large Writer documents and Libreoffice would perform an automatic save on one document and then while that was taking place start an automatic save with the second document. That is when the desktop would become unusable. Forcing a hard shutdown and reboot.

I do not have this problem now that I have 4 GB RAM. 

Regards

---

### Post by DuckHook on 2021-03-10
After an app crash, always useful to check your logs, esp apport, syslog, dmesg and systemd's journal.

---

### Post by Tupaq on 2021-03-10
> How much memory (RAM) does that rather old Dell Inspiron have?

I ran:

```
free -h
```

And this is what I got:

```
             total        used        free      shared  buff/cache   available
Mem:          3.7Gi       2.1Gi       308Mi       475Mi       1.3Gi       952Mi
Swap:         2.0Gi       400Mi       1.6Gi
```

---

### Post by Tupaq on 2021-03-10
Thanks for the advice, I'll do that if and when it happens again.

---

### Post by mastablasta on 2021-03-11
6.4.6 is quite stable. if the issue is only when saving to desktop, then don't save to desktop. it is not meant for files. use documents folder or a folder in /home to save files. this practise of saving files to desktop started in windows, but many people don't know that the more you save to desktop (in windows) the slower (general responsiveness) the whole thing gets. my colleague at work does that and with same machine as mine she had a very slow experience. i cleane dup the files, moved them to My Documents it was suddenly "fast" again.

you can also try installing a newer (Fresh) version via PPA: [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

in my case (kids used Fresh version as substitute for MS office for school work), it provided better compatibility with MS office, made better impress presentations and it opened faster.

---

### Post by tea for one on 2021-03-11
> **mastablasta said:**
> if the issue is only when saving to desktop, then don't save to desktop. it is not meant for files. use documents folder or a folder in /home to save files. this practise of saving files to desktop started in windows.

Probably this is the reason, as you mentioned in post 5 > Okay then I think I understand. I have had issues only on my desktop, where I also only have writer (.odt) files on my desktop. No crashes have occurred from opening .odt files elsewhere, such as in the "documents" or "downloads" folders accessed through the file manager.


As a default, Gnome 3 does not support saving files to the desktop.
However, you could try this extension [https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/](https://extensions.gnome.org/extension/2087/desktop-icons-ng-ding/)

---

