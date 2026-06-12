---
title: "New Linux user, need help"
date: 2008-03-20
forum: General Help
---

### Post by rogerdpenguin on 2008-03-20
I just installed linux using the wubi installer, which I have to say is very nice, I have windows xp and ubuntu linux running very nicely on a bootloader. I am a hardcore stepmania player, and I want it to be installed on linux, I am very new and don't know what to do. I got the tar.gz and extracted it to a folder on my desktop, now what do I do? How do I run the program?

---

### Post by kesman on 2008-03-20
Isn't there an executable file in the directory you just extracted? Doubleclick on it, or open up terminal and navigate yourself to the stepmania directory with:
```

cd /home/username/Desktop/stepmania

```
and run it with
```

./stepmania

```

or whatever the executable file is named.

---

### Post by rogerdpenguin on 2008-03-20
> **kesman said:**
> Isn't there an executable file in the directory you just extracted? Doubleclick on it, or open up terminal and navigate yourself to the stepmania directory with:
```

cd /home/username/Desktop/stepmania

```
and run it with
```

./stepmania

```

or whatever the executable file is named.

Yes there is an executable, double clicking it strangely enough didn't make it start. I navigated there with the terminal but it said no such file or directory.

---

### Post by kesman on 2008-03-20
Try running it from terminal and see if there's errors.

---

### Post by rogerdpenguin on 2008-03-20
Nope, still won't run.

---

### Post by lswest on 2008-03-20
right-click the file-->properties and under the permissions tab make sure the box "allow running as an executable" or so is checked, then it should work.

or the terminal way:
```
cd /home/<username>/Desktop/[name of stepmania folder]
chmod +x [executable file]
```

---

### Post by rogerdpenguin on 2008-03-20
> **lswest said:**
> right-click the file-->properties and under the permissions tab make sure the box "allow running as an executable" or so is checked, then it should work.

or the terminal way:
```
cd /home/<username>/Desktop/[name of stepmania folder]
chmod +x [executable file]
```

Still no luck ](*,)

---

### Post by Tomatz on 2008-03-20
Post me a link to it so i can download it. Then i can tell you what to do :)

---

### Post by rogerdpenguin on 2008-03-20
> **Tomatz said:**
> Post me a link to it so i can download it. Then i can tell you what to do :)

Heres the link
[http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz](http://www.stepmania.com/download.php?file=downloads/StepMania-3.9a-linux.tar.gz)

---

### Post by Appak on 2008-03-20
Assuming that you have the folder from the archive in your link extracted directly to your desktop
from a terminal if you run
```
~/Desktop/StepMania-3.9/stepmania
```

you should get an error message or some other output if the  program does not work right away
please post what you get.

if it says Permission denied you need to change the permissions on it so that you can execute it
one way is
```
chmod +x ~/Desktop/StepMania-3.9/stepmania
```

if it gives errors about opengl you may need to check you video driver
```
glxinfo | grep rendering
```
you should be good to go if it shows
```
direct rendering: Yes
```
otherwise open

System>Administration>Restricted Drivers Manager
and check the box under enable next to your video cards' driver

you will need to restart
then try executing the program again

hope that helps

---

### Post by Tomatz on 2008-03-20
No installation needed.

Just do this:

Extract (if you havent already)

Move the stepmania folder to your home folder

R-click on the applications menu

Click "edit menu"

Highlight "games" and single click on one of the game launchers

Click "new item"

In the name field type "stepmania"

In the "command" field click "browse" then navigate to /home/YOURUSERNAME/stepmania then double click on the stepmania executable

Close windows YOUR DONE to run it go to the applications, games menu :)

---

