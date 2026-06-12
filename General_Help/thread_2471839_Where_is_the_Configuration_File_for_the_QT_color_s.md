---
title: "Where is the Configuration File for the QT color selector dialog"
date: 2022-02-10
forum: General Help
---

### Post by cyberhiker001 on 2022-02-10
I would like to configure the "Basic Colors" menu, but I cannot find the configuration file. The "Custom Colors" seems to be a global setting (same colors for different instances), and I cannot find that either. I am running into some files, but they are in a code that my text editor cannot handle. I imagine they are Python - what editor might I need if the file I am looking for is in Python, and what other help might I need?


[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290001&stc=1[/IMG]

---

### Post by norobro on 2022-02-10
> **cyberhiker001 said:**
> I would like to configure the "Basic Colors" menu, but I cannot find the configuration file.How are you accessing that QColorDialog? Are you programming using Qt? The colors for a Qt app are stored in ~/.config/QtProject.conf. >  The "Custom Colors" seems to be a global setting (same colors for different instances), and I cannot find that either.Yes, same colors for different instances per user.>  I am running into some files, but they are in a code that my text editor cannot handle. I imagine they are Python - what editor might I need if the file I am looking for is in PythonWhat editor are you using? As far as I know, most editors (vim, gedit, kate, mcedit) have syntax highlighting for python by default.> and what other help might I need?Without knowing what you are attempting, we can only guess.

---

