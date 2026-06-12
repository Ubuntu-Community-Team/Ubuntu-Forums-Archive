---
title: "Display not right in LibraOffice since upgrading to 18.04."
date: 2018-06-16
forum: General Help
---

### Post by irv on 2018-06-16
Not sure if this is the right place to post this, it is sore of general. The display in the LibraOffice is not Right. Here is a Screenshot of the window.
[ATTACH=CONFIG]280114[/ATTACH]
No text displays in the top part of the window. 

Any idea how to fix this one, or is it a bug in LibraOffice?

---

### Post by PaulW2U on 2018-06-16
> **irv said:**
> Any idea how to fix this one, or is it a bug in LibraOffice?
Hi irv, this is the first time that I've seen this issue reported.

Have you tried any of the following?

[LIST]
[*]Logging in as another user, assuming that you have multiple users set up.
[*]Deleting or temporarily renaming your LibreOffice profile and letting LibreOffice create another default profile.
[*]Changing your current theme to another using GNOME Tweaks.
[/LIST]
I've been using two installations of Ubuntu 18.04, both of which started out as Ubuntu 17.10, and I don't see this issue.

---

### Post by irv on 2018-06-16
I think I just got to the bottom of the problem.
First, I did an upgrade from 17.10.1 to 18.04 and for some reason, it didn't install Office suites. So it didn't have all the files it needed. I went to the software app and it said that office was not installed. So I installed it and this fixed the problem, but now I have two packages installed. I think I need to do a complete removal and then reinstall it.

---

### Post by irv on 2018-06-16
This did the trick.
I completely uninstalled both versions of Libreoffice and reinstalled it fresh and now I have one package and it is working the way it should.
Here is a screenshot of the Writer. 
[ATTACH=CONFIG]280115[/ATTACH]
I will mark solved.

---

