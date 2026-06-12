---
title: "OpenOffice - Language pack"
date: 2005-06-22
forum: General Help
---

### Post by jemt on 2005-06-22
Hi experts.

I can't make OpenOffice understand, that I wan't danish spell checking. I have installed the following packages using apt-get :

 - openoffice.org-l10n-da
 - openoffice.org-hyphenation-da

I have selected 'Danish' i all combo boxes under Tools > Options > Language Settings - but I still don't have danish spell checking. What's wrong ?

 - Thanks :)

---

### Post by jemt on 2005-06-22
(Using OpenOffice 1.1.3 on Ubuntu 5.04)

---

### Post by jemt on 2005-06-22
I also have some problems with my characters. I am able to use 2 of the 3 speciel danish characters - the 3rd can't be used. It just gives me something like this []

---

### Post by angkor on 2005-06-22
do you have this installed:

myspell-da - The Danish dictionary for myspell

sudo apt-get install myspell-da

edit: btw does anyone know why the Dutch myspell package is not in the standard Ubuntu repos?

---

### Post by jemt on 2005-06-22
Ah yes - of cause! Forgot all about MySpell :)
 - Thanks !

I'm used to Words way of handeling the dictionary. Do you know how I turn off (only for the active document) the spell checking for all other languages then Danish? Right now I haft to right click every single word and mark it as "danish" in order to remove the red line under the word.

---

### Post by jemt on 2005-06-22
Hmm, It still didn't fix the problem with my danish letters. Is there a setting some where that enables me to set a character encoding ?

---

### Post by moises on 2005-07-05
[QUOTE=jemt]Hmm, It still didn't fix the problem with my danish letters. Is there a setting some where that enables me to set a character encoding ?[/QUOTE]
I'm having a similar problem with the OO1.1.3. It shows a square [] where a special character should appear.
I've got the AMD64 installation with myspell-ca and myspell-es installed. The documents with problems have been created from OO in the Windows version and are stored in a fat32 partition ([/etc/fstab]: /dev/hdb1       /mnt/users      vfat    user,auto,umask=000,utf8        0 0)
Any idea?

---

### Post by moises on 2005-07-06
Finally I think I've found the reason why: it was a problem with fonts! I've just changed the original Arial for Times and all the especial characters replaced the squares!
Hope that works also for you jemt

[QUOTE=moises]I'm having a similar problem with the OO1.1.3. It shows a square [] where a special character should appear.
I've got the AMD64 installation with myspell-ca and myspell-es installed. The documents with problems have been created from OO in the Windows version and are stored in a fat32 partition ([/etc/fstab]: /dev/hdb1       /mnt/users      vfat    user,auto,umask=000,utf8        0 0)
Any idea?[/QUOTE]

---

