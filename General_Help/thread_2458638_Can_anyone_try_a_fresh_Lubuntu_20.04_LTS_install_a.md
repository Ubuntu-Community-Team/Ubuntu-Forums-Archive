---
title: "Can anyone try a fresh Lubuntu 20.04 LTS install and test LibreOffice for me please?"
date: 2021-03-01
forum: General Help
---

### Post by mikeymikec on 2021-03-01
- edit due to thread merging -

Reiterating post #6:

I think I've found that the version of LibreOffice that comes with Lubuntu 20.04 LTS cannot print anything correctly at all, nor can it export to PDF correctly.

If I just do a quick Writer document, write 'test' in it and export to PDF, I get a blank page. 

---
OP:
The Ubuntu test page prints fine, a PDF prints fine, LibreOffice doesn't.  I have Epson's recommended driver installed, and I can print with Xubuntu 20.04 in a VM with LO to that printer without any trouble using the same driver.  If I try the same with my spare Lubuntu 20.04 VM, I get the same problem.  It's not a document issue, I'm printing the same document in the VMs or the host, or just printing 'test' from LO Writer.

I've tried using the driverless 'driver', or changing the communication method, but Lubuntu LO prints garbage no matter what.

Any help would be much appreciated.

---

### Post by CelticWarrior on 2021-03-01
If you have the snap version of Libreoffice you need to enable specific permissions. You can use Ubuntu Software for that, just open the software's page and you'll see a big red "Permissions" button.

---

### Post by mikeymikec on 2021-03-01
No, I'm just using what came with each respective version.  I also tried the latest stable 7.0 version on the host PC, which didn't help.

---

### Post by CelticWarrior on 2021-03-01
Libreoffice doesn't "come" with Lubuntu, last time I checked. It is installed by the user and then it can be either the traditional version in the repository or a snap.
Please check with
```
snap list
```

---

### Post by mikeymikec on 2021-03-01
I've just done a quick install of Lubuntu 20.04 LTS in another VM and I can confirm that it comes with LibreOffice 6.4.4.2.

---

### Post by mikeymikec on 2021-03-01
I started this thread:
[https://ubuntuforums.org/showthread.php?t=2458638&p=14023606](https://ubuntuforums.org/showthread.php?t=2458638&p=14023606)

But since then I think I've found that the version of LibreOffice that comes with Lubuntu 20.04 LTS cannot print anything correctly at all, nor can it export to PDF correctly.

If I just do a quick Writer document, write 'test' in it and export to PDF, I get a blank page.

---

### Post by howefield on 2021-03-01
Duplicate threads merged.

---

### Post by guiverc on 2021-03-01
Libreoffice has a few bugs when used with Qt (thus KDE(Kubuntu) & LXQt(Lubuntu)).

These impacted printing, and exporting to PDF the most (eg. [https://bugs.documentfoundation.org/show_bug.cgi?id=125234#c11](https://bugs.documentfoundation.org/show_bug.cgi?id=125234#c11) which was mentioned in the release notes [https://lubuntu.me/focal-2-released/](https://lubuntu.me/focal-2-released/)) 

I rarely print (esp. from Libreoffice) so haven't kept up, but I thought updates fixed this (the snapped version of LibreOffice prints anyway as it doesn't use the Qt components where the bug was). There are work arounds too (passing parameters to LibreOffice when it starts)

I can't find an easy paste to provide ; but [https://discourse.lubuntu.me/t/printing-problem-with-20-04/964/34](https://discourse.lubuntu.me/t/printing-problem-with-20-04/964/34) maybe helpful. 

(I think it was starting with something like

```
Exec=env SAL_VCL_QT5_USE_CAIRO=true libreoffice --writer %U
```

(it worked for all of us who tried it, even better maybe added it to environment variables as per [https://discourse.lubuntu.me/t/printing-problem-with-20-04/964/44](https://discourse.lubuntu.me/t/printing-problem-with-20-04/964/44) but sorry it's been awhile since I looked at printing issues so can't recall everything clearly)

---

### Post by mikeymikec on 2021-03-02
Thanks for your response.  Late last night I also found this solution:

[https://ask.libreoffice.org/en/question/242188/cannot-print-anything-exporting-to-pdf-produces-blank-pdf-lubuntu-2004/](https://ask.libreoffice.org/en/question/242188/cannot-print-anything-exporting-to-pdf-produces-blank-pdf-lubuntu-2004/)
```

sudo apt remove libreoffice-qt5

```

It fixed both the print and PDF issues for me.

---

