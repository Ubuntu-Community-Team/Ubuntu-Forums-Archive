---
title: "(Almost) absolute beginner questions: startup applications and extensionless files"
date: 2008-04-27
forum: General Help
---

### Post by Azrael Strife on 2008-04-27
Hey there, just got Ubuntu 8.04 installed today, I think congratulations and thanks are in order to everyone working on Ubuntu, you've done an amazing job and seem to have succeeded at finally setting me free from my Windows dependency (hopefully it'll stay that way), now onto the questions!

1. How can I set up apps to start at system startup? I'd like Pidgin, among others, to launch along with Ubuntu, but haven't found the way to do it.

2. How can I open an extensionless file, like a README? I doubleclick and it asks me what program to use to read it but the list is empty.

Thanks in advance.

edit: since I'm at it, I'll throw another question, so I don't clog the forums with threads.
3. How can I set, for example, Amarok, to play mp3 files by default? the default one crashes when I try to move forward or backwards the mp3 file rather erraticaly (Totem)

---

### Post by scragar on 2008-04-27
System>Preferences>Sessions -- start-up apps is the first tab(selected by default :P)

click custom, and enter```
gedit
``` after that it should automaticly use gedit(the default text editor) from then on.

---

### Post by Azrael Strife on 2008-04-27
Great, now another question, if you don't mind.

3. How can I set, for example, Amarok, to play mp3 files by default? the default one crashes when I try to move forward or backwards the mp3 file rather erraticaly (Totem)

4. How can I find out where my apps are installed? say I want to use a specific program for opening a determined file type and its not on the list, where do I look?

---

### Post by Monicker on 2008-04-27
One good way to find out what kind of file you are dealing with is to use the "file" command from the terminal:


```
arkaic@arkaic-laptop:~$ file /etc/init.d/README

/etc/init.d/README: UTF-8 Unicode English text
```


You should be able to get the similar info in the gui by right clicking the file and going to properties.

---

### Post by daimaru on 2008-04-27
for any file to set the default application to open with. right click the file select properties choose the "open with" tab and select the program you want to open the file extension with.

oh and to find out where a program is : for example audacious for mp3 playback type in terminal:

```
whereis audacious
```

---

### Post by scragar on 2008-04-27
all launchers for programs(with around 10 exceptions in the whole world :P) can be found in /usr/bin , but since this contains a lot of files, and by default a program name on it's own would reference here you can often just enter the program name when prompted to find it(like when you asked the second question, the 'gedit' file is actualy located in **/usr/bin/gedit**, yet entering **gedit** on it's own worked perfectly.)

---

### Post by Azrael Strife on 2008-04-27
Thank you all! :)

---

### Post by gnivler on 2008-05-08
Is there a switch or something that will make the startup applications only appear in the notification/tray area?  I'm specifically using Mobloquer and Pidgin, they open a GUI window and tray icon simultaneously but I'd prefer to have them hidden at startup.  Minor, definitely.

:redface:

---

### Post by jimtb on 2008-05-08
> **gnivler said:**
> Is there a switch or something that will make the startup applications only appear in the notification/tray area?  I'm specifically using Mobloquer and Pidgin, they open a GUI window and tray icon simultaneously but I'd prefer to have them hidden at startup.  Minor, definitely.

:redface:

I think that this is somewhere in pidgin's options. As for mobloquer, just execute it with the --tray console argument to start it minimized in tray. So instead of executing 
```
mobloquer
```
Execute
```
mobloquer --tray
```

Hope that helps.

:-)

---

### Post by gnivler on 2008-05-08
You are the man, thank you.  I was thinking maybe it wasn't application specific, but with that in mind I can look more appropriately.

cheers

---

