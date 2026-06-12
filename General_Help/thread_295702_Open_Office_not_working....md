---
title: "Open Office not working..."
date: 2006-11-08
forum: General Help
---

### Post by recrispi on 2006-11-08
Hello Everybody!

I got a strange error with openoffice. I was working on a spreadsheet with 3 graphs and suddenly OO crashed. So I went with the routine of restoring the files, but when doing so, OO crashed again and now it does not start. It displays an error message in a window:
> The application cannot be started.
An internal error occurred:confused: 
but when I look at the running processes I find this:
> 4061 ?        S      0:00 /bin/sh /usr/lib/openoffice/program/soffice -calc
 4072 ?        S      0:01 /usr/lib/openoffice/program/soffice.bin -calc

it's running and eating some memory.
Then I ran OO from commandline to see if could get some more information about the error and I got this:
> [Java framework] Invalid file for shared Java settings.javaldx failed! 
[Java framework] Invalid file for shared Java settings.

So how does OO crash did damage java in some way? :-k and most important: how can I fix this error? I need OO to complete some spreadsheets in my office.:( 
Thanks for any help you could give me.

By the way, I'm using xubuntu-6.06-alternate-server install with openbox, my kernel is 2.6.15-26-386, Openoffice 2.0.2-2ubuntu1 with spanish language added (from repositories), and java installed is java-common 0.24ubuntu2 and java-gcj-compat 1.056-0ubuntu.

---

### Post by canadianwriterman on 2006-11-08
Shut down all instances of OpenOffice (you may have to reboot). Check to see if OpenOffice is picking up your Java by going to Tools > Options > OpenOffice.org > Java. If it doesn't list Java there, you'll need to use the Add button to point it to your Java.

---

### Post by recrispi on 2006-11-09
> **canadianwriterman said:**
> Shut down all instances of OpenOffice (you may have to reboot). Check to see if OpenOffice is picking up your Java by going to Tools > Options > OpenOffice.org > Java. If it doesn't list Java there, you'll need to use the Add button to point it to your Java.

How can I do it from commandline? I do not have XFCE installed.
Thanks for your help.

---

### Post by canadianwriterman on 2006-11-09
You don't to have XFCE installed. As long as you can open OpenOffice, the settings are done there.

---

### Post by recrispi on 2006-11-10
> **canadianwriterman said:**
> You don't to have XFCE installed. As long as you can open OpenOffice, the settings are done there.

Sorry, but I can't open Openoffice. When I try to ru openoffice I got the error messages and there is no openoffice window opened, but the process is running in the list, eating resources.
Should I reinstall Openoffice from scratch?
Thank you.

---

### Post by recrispi on 2006-11-10
> **recrispi said:**
> Sorry, but I can't open Openoffice. When I try to ru openoffice I got the error messages and there is no openoffice window opened, but the process is running in the list, eating resources.
Should I reinstall Openoffice from scratch?
Thank you.

Well, I uninstalled Openoffice completely (even configuration files) using synaptic. Then I reinstalled it and it's now working again :-D 
It offered to recover the file I was working on when it crashed, but I preferred to lose that archive and work from an older version (to avoid OO crashes again).
Thanks for your help, canadianwriterman

---

### Post by canadianwriterman on 2006-11-12
Glad you got it running again, recrispi.

---

