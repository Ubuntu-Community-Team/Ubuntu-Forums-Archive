---
title: "SCIM problems in Fiesty"
date: 2007-04-28
forum: General Help
---

### Post by mskadu on 2007-04-28
Hi,

I am trying to use SCIM to input Devanagari (Indic) scripts. However, I am unable to get a list of avialable inputs when i press ctrl+space. Here's what i have done so far:

[LIST=1]
[*]ensured that scim packages are installed
[*]ensured that the relevant language support is installed (I am not sure if this is requiredm but just in case)
[*]Added the following command to my session startup-manager:
```
/usr/bin/scim -f x11 --no-socket -d
```
[*]and then restarted my machine.
[*]When i log back in, i have a scim icon sitting in my system tray
[*]I start Firefox and press Ctrl+Space
[*]Nothing happens :confused:[/LIST]What am i doing wrong? Any help is appreciated. I have already tried the IRC channel and the community docs/ guides.

---

### Post by thnhan on 2007-04-29
Check this link, it might help

[https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM)

From the document:
Note : You should already be able to use SCIM input in a few applications, like gedit (Application>Accessories>Text Editor), by right clicking on the document, then selecting Input Methods>SCIM Input Method. However, it won't work in the others, like Open Office.

The recommended method to set up SCIM input for all applications is using a command-line tool called im-switch (where im stands for Input Method, obviously :) ). Before that, you will have to know the name of the locale you're using. In a terminal (Applications>Accessories>Terminal) ...

---

### Post by mskadu on 2007-04-29
Thanks for the link. The content seems to have changed the last time i checked it. Let me go through the newly added steps.

I have a question. Do i need to run im-switch everytime i need to change a language. The way i thought this works is that 

- you so scim-setup and enable the languages you want. 
- You need to have support installed for those languages before-hand though.
- Then whenever you are in your application, say gaim and you want to type in, say Greek, 
- you simply switch on the scim mode (ctrl+space - as setup in scim-setup) 
- and then select a language from the scim icon sitting in your notification area (system tray) 
- and start typing.

Repeat the process and select english when you want to come back to typing english? Is this incorrect? :confused:


I will be soon setting this up for non-techie users. I cant ask them to type im-switch everytime they want to change language.

Any suggestions/ corrections welcome :)

---

### Post by thnhan on 2007-04-30
I do the im-switch only once.

NT

---

