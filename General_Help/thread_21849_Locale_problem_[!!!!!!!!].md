---
title: "Locale problem? [!!!!!!!!]"
date: 2005-03-24
forum: General Help
---

### Post by Failing_fast on 2005-03-24
Could anybody tell me what this error means : 


"current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultThe installer is unable to run in graphical mode."

i get a variant of the same error whenever i try to install anything with  a java front end...

does anyone know how to change the locale in x11??
iv tried the config files but cant find anything even like it..

the LANGUAGE is set to "LANG=en_IE.UTF-8"
iv tried unsetting it but nothing changed.. 

does anyone have any suggestions, i would greatly appreciate the advice  [-o<  :!:

[edit] Just to note ive changed the latest java version installed, (the java graphical installer itself crashed with the same error) [/edit]

---

### Post by zipman on 2005-04-12
I have the same problem.
Can anyone provide us with a solution?

---

### Post by andyk on 2005-04-12
on the same lines, i'm trying to build a script for starting LimeWire, rather than going through CLI everytime.  when i opened gedit from command line i got:

(gedit: 7363): GTK-Warning**: Locale not supported by C library.
                       Using default "C" locale.

also get the same error for GDK.

edit:  i just noticed on boot up that i'm getting locale problems in LC_MESSAGE, and other LC_locations. just noticed this today.  yesterday i installed a unstable/testing version of libc6 prior to installing xmms plugins.  quinky-dink ?

any help ?

andy

---

### Post by EzraBrowser on 2005-04-13
I'm new to Unix/Linux, so the information below should be read with that in mind.

I recently upgraded from Warty to Hoary using Synaptic Package Manager smart upgrade without reading the instructions.  Many package upgrades failed, the initial problem being that the default C locales were being used rather than en_GB.  I tried regenerating them with locale-gen but it failed with a syntax error on line 1775 in /usr/share/i18n/locales/translit_cjk_compat.  I edited this to change the initial "e" to "%" (comment).  I then edited /etc/locale.gen to include only the definition for en_GB.UTF-8.  locale-gen then completed successfully. One problem down, several to go.  I think the next task is to edit etc/environment to specify en_GB.UTF-8.

Amazingly, most of my system seems to be up and running.

I tried to raise a bug report for the package delivering the translit... file (locales 2.3.2.ds1-20ubuntu13 [unlucky for some!]) but the link to the How-to and bugzilla did not work.

Ez
P.S. Changing the (three) locales in /etc/environment solved my locales problem.

---

