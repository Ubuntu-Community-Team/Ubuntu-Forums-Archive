---
title: "Input áéíóú in tty console"
date: 2008-07-03
forum: General Help
---

### Post by bagm on 2008-07-03
Hi,
  I can't input áéíóú in the tty console, but I can input ¡ñÑ.
  And all of these characters are displayed correctly.
  Any help will be greatly appreciated.

---

### Post by polmir on 2008-07-03
Type in terminal```
locale
```and post output.
	
What is your language?

---

### Post by bagm on 2008-07-03
> **polmir said:**
> Type in terminal```
locale
```and post output.
	
What is your language?

LANG=en_US.UTF-8
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC="en_US.UTF-8"
LC_TIME="en_US.UTF-8"
LC_COLLATE="en_US.UTF-8"
LC_MONETARY="en_US.UTF-8"
LC_MESSAGES="en_US.UTF-8"
LC_PAPER="en_US.UTF-8"
LC_NAME="en_US.UTF-8"
LC_ADDRESS="en_US.UTF-8"
LC_TELEPHONE="en_US.UTF-8"
LC_MEASUREMENT="en_US.UTF-8"
LC_IDENTIFICATION="en_US.UTF-8"
LC_ALL=

My language is Spanish.

TIA.

---

### Post by bagm on 2008-07-03
My country is Argentina.

---

### Post by polmir on 2008-07-04
Install packages
```
sudo apt-get install console-data console-terminus
```
and set the Spanish version of the keyboard.

[Argentina forum team]("http://ubuntuforums.org/forumdisplay.php?f=189")

---

### Post by bagm on 2008-07-04
> **polmir said:**
> Install packages
```
sudo apt-get install console-data console-terminus
```
and set the Spanish version of the keyboard.

[Argentina forum team]("http://ubuntuforums.org/forumdisplay.php?f=189")

But my keyboard is US International (with dead keys)... not Spanish.

TIA.

---

### Post by polmir on 2008-07-05
My keyboard is also US International (with dead keys) not Polish.

To write special characters appropriate for my language (Polish) I use the right Alt key + letter. 
For example:
Alt+a = &#261;
Alt+c = &#263;
Alt+e = &#281;
Alt+l = &#322;
etc
For the other languages are similar. Only English does not require additional key. If you set the Spanish keyboard will be able to write well in English as yet.

[http://en.wikipedia.org/wiki/British_and_American_keyboards#Microsoft_Windows]("http://en.wikipedia.org/wiki/British_and_American_keyboards#Microsoft_Windows")

[http://ubuntuforums.org/showthread.php?t=449598]("http://ubuntuforums.org/showthread.php?t=449598")

---

### Post by bagm on 2008-07-05
I'm still at a loss with this issue.
In the tty console, I can see characters áéíóúñÑ, but I can't input áéíóú.
Any help will be greatly appreciated.
TIA.

---

### Post by der_joachim on 2008-07-06
Working with deadkeys has always been horrible for me. I did find an alternative though: compose keys.

The idea is quite simple (and apparently quite old as well). If you want to make an é, you just press Compose+'+e. A ñ is created by Compose+~+n.  The good news is that the console supports XkbOptions which makes it a breeze to configure (and you can configure xorg the same way). The bad news is that I am currently not at my Ubuntu box. If you'd like to try compose keys, just let me know and I'll post my config files later.

---

### Post by bagm on 2008-07-06
> **der_joachim said:**
> Working with deadkeys has always been horrible for me. I did find an alternative though: compose keys.

The idea is quite simple (and apparently quite old as well). If you want to make an é, you just press Compose+'+e. A ñ is created by Compose+~+n.  The good news is that the console supports XkbOptions which makes it a breeze to configure (and you can configure xorg the same way). The bad news is that I am currently not at my Ubuntu box. If you'd like to try compose keys, just let me know and I'll post my config files later.

Thanks. I still prefer just pressing 'a to get an á, AtlGr+n to get an ñ, etc.
I'm still at a loss with my tty console accents.

---

