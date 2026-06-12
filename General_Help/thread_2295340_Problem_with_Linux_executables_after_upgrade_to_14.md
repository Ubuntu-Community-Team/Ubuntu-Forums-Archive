---
title: "Problem with Linux executables after upgrade to 14.04"
date: 2015-09-17
forum: General Help
---

### Post by mje1708 on 2015-09-17
Hi

I have been using an ebook provided by Pearson Education on Ubuntu 12.04 without problems. To start the ebook you simply click on an executable file and the ebook runs (It has nothing to do with Windows - so not a Windows .exe file). However since upgrading to Ubuntu 14.04 the file won't run anymore. I have checked the file permissions to give it permission to run but still nothing happens.

I have read elsewhere that this may be because the partition on which the file is sitting does not allow executable files. However I had no problem with the previous version of Ubuntu and didn't select any different options when I installed 14.04 (I did a clean install reformatting discs and everything). If this is true and I do not know how to check if it is true, how do I modify it.

Any ideas anyone?

Thanks in advance for your help.

Mje1708

---

### Post by monkeybrain20122 on 2015-09-17
Well that is pretty little information to go by without knowing what kind of file it is. What if you start running the program in the terminal, do you get any error message?

---

### Post by mje1708 on 2015-09-18
Hi

I appreciate that it is pretty little information. Unfortunately I know very little about what kind of file it is. It was provided with the ebook and just worked from the start when I used 12.04. I asked Pearson the publishers about it and unfortunately they don't know anything either. Even their technical department can't help - they only know about the Windows version. 

How can I find out what sort of file it is? Also I don't know how to run it in the terminal. I always just double-clicked on it from the desktop. Could you give me the command to use in the terminal?

Sorry to be dim!

Thanks

Mje1708

---

### Post by pauljw on 2015-09-18
Try opening the menu at the top right corner of your screen (looks like a gear), select About This Computer; Removable Media; Other Media; open the drop down menu for Type, select e-book reader, open the drop down menu for action and select Other application and scroll down to and highlight document viewer, click on select and close.  See if you can read your e-book now.

---

### Post by monkeybrain20122 on 2015-09-18
> **mje1708 said:**
> 

How can I find out what sort of file it is? Also I don't know how to run it in the terminal. I always just double-clicked on it from the desktop. Could you give me the command to use in the terminal?



Right click it, choose properties and it should tell you what kind of file it is.  Is there a free sample that can be downloaded?

It is not clear from your OP whether the "ebook" itself is executable or that it is a normal ebook (e.g EPUB) that requires an ebook reader (the executable) to open.

---

### Post by mje1708 on 2015-09-18
Possibly I have misled you by describing it as an ebook. Basically the package it is a conventional book with comes with a DVD. The DVD contains an electronic version of the book. So when you open it on your PC you see a representation of the normal printed book on your screen which you can navigate through like a normal book. The difference is that you can click on sound clips and hear them. You can click on video clips and hear them. It has hyperlinks etc. So to answer monkeybrain's question, it is the ebook itself which is executable.

The DVD contains both a windows version and a linux version. The "program" can be installed onto your computer using either Linux or Windows. The only difference being that you still require the DVD to run the Windows version (obviously to try and avoid copying it without paying). However with the Linux version once "installed" (in actual fact with Linux you only have to copy the contents of the DVD onto your PC) you no longer require the DVD. You execute the electronic book program simply by clicking on the executable file.

It worked without any problems on 12.04 but now on 14.04 it no longer works. So obviously something has changed between the two versions of Ubuntu.

If I right click on the file in properties it says 

executable (application/x-executable)

---

### Post by sotiris2 on 2015-09-18
Is the actual executable sitting on the Desktop or just a shortcut? If it sitting on the Desktop you can get to it in a terminal by ```
cd ~/Desktop
``` Otherwise you may have open in terminal if you right click the folder containing it. If that doesn't exist copy the location of the file from its properties menu (start from the first / ) and in a terminal write cd leave one space and paste the location (with Ctrl+Shift+V not just Ctrl+V). 

Any ONE of those methods will get you a terminal pointed in the right directory. Then do ```
./name_of_executable
``` That is a dot a slash / and the name of the executable file. If you get any messages post them here.

---

### Post by mje1708 on 2015-09-18
I navigated into the folder where the executable is and get this -

mike@asus-e810:~/Elementary/DATA$ ./START_Linux
./START_Linux: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory

---

### Post by sotiris2 on 2015-09-18
Try ```
sudo apt-get install libgtk2.0-0
```

---

### Post by mje1708 on 2015-09-19
Thanks for the suggestion sotiris2. Unfortunately it has no effect.

---

### Post by sotiris2 on 2015-09-19
Did you run the program from the terminal again? If so is it exactly the same message? It is possible that another library is missing or that indeed I didn't tell you to install the right package. Can you post the output of ```
file ./START_Linux
``````
ldd ./START_Linux
``````
arch
``` Where program is the ebook/executable file. 
There is a chance that START_Linux is not the actual executable but a script that launches it.  If the first command, file, says its a Bourne-Again shell script or something similar can you please post its contents here?

---

### Post by monkeybrain20122 on 2015-09-19
You may need the 32 bit version of libgtk2.0-0

```
sudo apt-get install libgtk2.0-0:i386
```


Either that or you may need to make a symkink to /usr/lib. I don't remember what 12.04's lib structure looked like. But try the above first. If not work 
```
sudo ln -s  /usr/lib/i386-linux-gnu/libgdk-x11-2.0.so.0  /usr/lib/libgdk-x11-2.0.so.0
```
if not work still

```

sudo rm  /usr/lib/libgdk-x11-2.0.so.0

sudo ln -s  /usr/lib/x86_64-linux-gnu/libgdk-x11-2.0.so.0  /usr/lib/libgdk-x11-2.0.so.0


```

---

