---
title: "Help with Alien"
date: 2006-10-26
forum: General Help
---

### Post by SmiLey497 on 2006-10-26
im trying to convert the rpm into a deb but it keeps saying file not found:(

---

### Post by llamakc on 2006-10-26
The quickest way to get help is to cut-n-paste the command and error message here.

---

### Post by SmiLey497 on 2006-10-26
this help?
> z@z-desktop:~$ sudo alien -d bitpim-0.9.07-0.i386.rpm
File "bitpim-0.9.07-0.i386.rpm" not found.

---

### Post by llamakc on 2006-10-26
bitpim is in the repositories:

Enable universe and install from there. Otherwise, is that rpm package on your ~/Desktop and not in ~ where you're trying that command?

Make sure you're in the directory when calling alien without a path to the rpm.

---

### Post by SmiLey497 on 2006-10-26
its in the desktop, the bitpim in synsaptic is 0.9.04, the newest version is 0.9.07 which is what i wanted to install

---

### Post by llamakc on 2006-10-26
cd ~/Desktop

and rerun your command.

---

### Post by cp1969 on 2007-12-16
I'm having the same problem now and rather than make a new thread, I'll just post in this one.  
I, too, am trying to make a .deb from a .rpm which resides on my desktop.  What I'm trying to do is make an Epson CX8400 printer work.


Here is what happened:

cep@cep-desktop:~$ cd ~/Desktop
cep@cep-desktop:~/Desktop$ sudo alien pipslite-cups-1.0.1-1.i386.rpm
Warning: Skipping conversion of scripts in package pipslite-cups: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.
pipslite-cups_1.0.1-2_i386.deb generated
cep@cep-desktop:~/Desktop$ 

Couple questions:  What does the warning about skipping the conversions of scripts mean? Second, it looks as though a deb was generated, but where is it?  It isn't on the desktop.

Thanks.

edit:  I should add that I have tried the search function but obviously don't know how it works.  I ask it to search for "pipslite" as a Debian file and it finds nothing even though there is a .deb file on my desktop.

Never Mind!  After consulting the help function, I found out how to find the .deb files.  AND, I discovered that it overwrote the existing .deb I already had, so all is temporarily well.  I'm off now to install it.  Probably be back in about two minutes.

---

### Post by darrengoddard on 2008-01-01
i'm having similar problems installing an epson stylus dx8450 all-in-one printer.  i downloaded the .rpm file and managed to create the .deb file using alien (i too saw the scripts warning but just ignored it!) and then installed the package using kpackage.  

all seemed to be well but when i went to the printers section of the KDE control centre to install the printer i could not find it.

in desparation i tried a number of other drivers until i found one that appeared to work - epson stylus colour 870.  i don't know if the machine is working properly yet - i haven't tried the copy or scanner functions yet but i'm confused.  surely by installing the deb file the printer would have appeared in the list.

is it possible that i am doing something incredibly stupid or is there a piece of the jigsaw that i am missing?

any advice would be greatly appreciated

darren

UPDATE UPDATE UPDATE UPDATE UPDATE UPDATE 

following another root around the forum i've found the answer and implemented it.  navigate your way to a thread called " Epson Stylus CX8400 - Is there anyone who has been successful?"  and there you will find the answer to my problem and hopefully yours.

darren

---

