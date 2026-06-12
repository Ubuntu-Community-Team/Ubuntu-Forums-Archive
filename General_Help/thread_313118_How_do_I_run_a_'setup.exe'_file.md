---
title: "How do I run a 'setup.exe' file"
date: 2006-12-05
forum: General Help
---

### Post by noob4now on 2006-12-05
I have a programme i want to install but when I click on the setup.exe file i get the following error message 'Cannot open setup.exe: No application suitable for automatic installation is available for handling this kind of file.

Does anyone know what i need to install with my Ubuntu OS to get it to run?

Any help much appericated

---

### Post by eriefisher on 2006-12-05
That looks like a Windows program???

It won't work on linux.

---

### Post by Dubbayoo on 2006-12-05
it might help to know what the program is and if you have wine installed.

---

### Post by Shatrat on 2006-12-05
A program written for windows will only run in windows.  
There is a program you can easily install called WINE which will allow you to run many windows programs in linux.  You can do a little googling to find out if it will work with whatever you are trying to install, and how to use wine.

---

### Post by Circus-Killer on 2006-12-05
goto [http://www.winehq.com/]("http://www.winehq.com/") and click on "AppDB". then you will see a textbox on the bottom left. type in the app you wanna run and click search. if someone has tested and submitted results, you should get an indication if it will run in wine or not.

---

### Post by srirammurali on 2006-12-05
use wine to run the exe..
[SIZE=4]
[COLOR=Magenta]sudo apt-get install wine  :KS[/COLOR][/SIZE]

---

### Post by lucky_chouhan on 2006-12-05
use command -

root@root#wine realplayer.exe

---

### Post by tech9 on 2007-12-21
> **eriefisher said:**
> That looks like a Windows program???

It won't work on linux.

correction!

it will work - with a program call wine

---

