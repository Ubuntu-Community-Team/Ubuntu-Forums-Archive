---
title: "Konqueror tab bar and Javascript"
date: 2008-02-09
forum: General Help
---

### Post by marciano#1 on 2008-02-09
How can I set window.open or any related javascript functions to let users open a pop up window without the tab bar in Konqueror?

For example, this command works fine in Safari, IE, Firefox-Ubuntu but Konqueror

[COLOR="Blue"]"window.open('http://google.com','','width=300,height=200,status=no,menubar=no. location=no,toolbars=no,scrollbars=no,resizable=no,directories=no,location=no,copyhistory=no')"[/COLOR]

Height size includes the tab bar, so the free space is less than the regular behavior, that affect my need. 
Thanks in advance for any help.

---

### Post by CupofDice on 2008-02-09
Have you tried unchecking "Open popups in new tab instead of in new window" in Settings/Configure Konqueror/General? Also check out Settings/Configure Konqueror/Java & Javascript/Javascript and check allow on "Open new windows". Hope that helps.

---

### Post by marciano#1 on 2008-02-09
Maybe I was not clear.
I am developing a new website.
I am debugging it in Win-IE, MAC-Safari, Firefox-Ubuntu and Konqueror and having problems with the last one.  These pop-ups only have the title bar but Konqueror adds the tab bar by default except those users that have tab bar disabled. 
I can 'ask' for the user's browser and add some pixels height in Konqueror's case but this is not an elegant way.
Thanks!

---

