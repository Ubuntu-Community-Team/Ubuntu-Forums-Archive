---
title: "Libre Office Help opens in Firefox but not in Brave on Ubuntu"
date: 2021-05-09
forum: General Help
---

### Post by nadrach on 2021-05-09
I posted the following query on AskLibO:

> LO 7.1.3 Help on Ubuntu 20.04 opens in Firefox (88.0) but not Brave (1.24.82). LO searching for "file:///tmp/<ident>.tmp/NewHelp0.html" returns "ERR_FILE_NOT_FOUND". Any suggestions as to why? I prefer Brave for it's security stance, especially with the advent of FLoC, so would like to keep it as the default, but to use LO Help, the default has to be Firefox. Bit of a pain. Help?

The reply was:

> LibreOffice is not searching for that file. LibreOffice passes the file location to the operating system / desktop manager and from that point on, it is the task of the operating system to start the proper application (and pass the file location) according to the MIME type. And LibreOffice has no preferences of the browser. LibreOffice even doesn't know which browser is being started.

So if this situation is not with Libre Office, next port of investigation is Ubuntu. Any suggestions?

---

### Post by grahammechanical on 2021-05-09
When an application makes a request to the operating system to open a file that is an internet address and a web page, then the operating system opens the default web browser. In Ubuntu the default web browser is Firefox. To change the default application open System Settings>Default Applications and select the Brave web browser from the drop down list.

Regards

---

### Post by nadrach on 2021-05-10
That's the problem.
Libre Office Help opens OK with Firefox. I changed the default browser to Brave (my own preference), but I cannot open LO Help in Brave. It returns "file not found".
So whenever I need to use the Help in LO I have to revert the default browser to Firefox, then set the default browser back to Brave afterwards.

---

### Post by deadflowr on 2021-05-10
Which brave?
The one from Ubuntu or the one from Brave's website?
The one from Ubuntu is snap package and does not have access to system files, or files outside of Home.

---

### Post by nadrach on 2021-05-10
That might explain things. It's the one from Ubuntu and therefore in trying to access "file:///tmp/<ident>.tmp/NewHelp0.html" (where <ident> appears to be randomly generated on a one-time basis every time you access the Help) it almost certainly is outside the access parameters. Hmm.

---

### Post by deadflowr on 2021-05-10
If it is the Ubuntu/snap version, you can try ditching it and follow Brave's instructions on adding their repositories and install that version.
See: [https://brave.com/linux/]("https://brave.com/linux/")

And see if that changes things for the better.

---

### Post by nadrach on 2021-05-10
Yes ... Fixed ... Thank you very much.
All working now.

---

