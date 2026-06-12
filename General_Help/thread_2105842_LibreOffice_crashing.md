---
title: "LibreOffice crashing"
date: 2013-01-17
forum: General Help
---

### Post by d4rk0wl on 2013-01-17
Hello everyone,
I have recentally run into a problem. I cannot seem to open Libreoffice. Upon loading it gets to the splash screen, loads for a few seconds and then quits. I have no error message associated with it and apport does not appear.
I am running an almost fresh install of Kubuntu 12.04, I have deleated the user-library per direction of the Libreoffice wiki to no effect. I have a hunch it has something to do with my java runtime. Here is the printout of the terminal when I run the program:
```

will@Kubuntu:/usr/bin$ ./soffice
[Java framework] Error in function createSettingsDocument (elements.cxx).
javaldx failed! 
Warning: failed to read path from javaldx
terminate called after throwing an instance of 'com::sun::star::uno::RuntimeException'

```

Any help on this matter would be appriciated, thanks in advance!
- D4rk0wl

---

### Post by ChadCurtiss on 2013-01-17
I would uninstall and re install Java completely. If that does not help try the same thing with libre office. I just updated from 12.04 to 12.10 but I never had any issues with Libre. Good Luck

---

### Post by ibjsb4 on 2013-01-17
No answer for you, but got some hits that may interest you.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=javaldx&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=javaldx&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by zombifier25 on 2013-01-17
Try deleting the folder ~/.config/libreoffice .

---

### Post by d4rk0wl on 2013-01-18
Thanks for the replies everyone but I managed to figure this out out, as said before I attempted to rename/move the .config file as called for by the Libreoffice wiki though that had no effect. I didn't pay attention to the fact that the onwer of the config file in my home directory was root:root. Didn't think that sounded to right

```
sudo chmod -vR will ~/.config/
```
Took care of the problem.

Regards,
- D4rk0wl

---

### Post by ajgreeny on 2013-01-18
Any idea how that happened, and how root became owner of the configuration folder?

Did you have to copy it as root from some other partition or disk?

---

### Post by d4rk0wl on 2013-01-19
I honestly have no idea. Libreoffice was working fine on the initial install and all of a sudden started to crash. This was a fresh install downloaded from kubuntu.org

I did not receive any error or apport report when it would crash, minus what I retrieved after running it from a terminal.


Though, one time I accentaly opened libreoffice when I was in a hurry and I spammed for it to quit, once again because I was in a hurry. Ever since then is when this problem arose.


Regards,
- D4rk0wl

---

### Post by sudodus on 2015-03-23
Thanks a lot :KS

This thread helped me solve a current problem with ToriOS-beta,

```
sudo chown -R $USER ~/.config
```

---

