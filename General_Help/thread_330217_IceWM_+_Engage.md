---
title: "IceWM + Engage?"
date: 2007-01-02
forum: General Help
---

### Post by forcesofhabit on 2007-01-02
It shows up on screen, but when I try and press 'Configuration' nothing happens, and I get the following error in Terminal:

```

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_get();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_get();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_get();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_get();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_get();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_get();

        With the parameter:

        hash

        being NULL. Please fix your program.
***** Developer Warning ***** :
        This program is calling:

        ecore_hash_set();

        With the parameter:

        hash

        being NULL. Please fix your program.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        This program is calling:

        ewl_config_get();

        With the parameter:

        cfg

        being NULL. Please fix your program.

***** Ewl Developer Warning ***** :
 To find where this is occurring set a breakpoint
 for the function ewl_print_warning.
        This program is calling:

        ewl_embed_engine_name_set();

        With the parameter:

        engine

        being NULL. Please fix your program.


```

Anyone have an idea what I can do to fix the problem??

---

### Post by 4KvRMU7Nnv on 2007-01-04
yes. with the recent version of engage, the configuration via right click will not work.  Nothing is wrong with your engage dock, thats just the way all of them are right now.  The only way to edit the dock is to change files in ~/.e/e/applications.  from there you can add icons in *.desktop format and change the order of the icons appearance in the dock in the "order" file.  If you want to change the way that it runs then you have to run it with the right parameters.  In the terminal type 

engage -R 0 -Z 2.5 -T 0 -H 200

Thats how I run my engage dock and it works great!  Don't forget that you must populate the ~/.e/e/applications/all file with the applications from /usr/share/applications file before you will see any icons.  From there you can change the icon by individually editing the *.desktop file.  Hope I helped some!

---

### Post by samae on 2007-01-05
I have the same problem with engage standalone and xfce4 ...
I hope the configuration button will soon be fixed ^^

---

