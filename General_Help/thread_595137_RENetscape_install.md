---
title: "RE:Netscape install"
date: 2007-10-28
forum: General Help
---

### Post by upthelum on 2007-10-28
Can anyone tell me how to install netscape. I have tried a few different methods but none seem to work and the installations forum doesn't seem to busy. I attached the dir that contains the files.

Any help would be great thanks...

---

### Post by ctsdownloads on 2007-10-28
Sure, no problem.

Dowload the package. Once downloaded, right click and "extract here".

Inside the new folder called navigator, look for "navigator" again, as this is the file to run the program. See, it's a self contained program, all inside one folder as not to touch your OS. Now let's make it less of a hassle to use.

Noting the path to the folder, in my case it is:
> /home/matt/Desktop/navigator

I go back to the desktop. I right click and choose "create a launcher". Leave it set to application and give it a name. Then browse to 

> /home/matt/Desktop/navigator



 I enter 

> /home/matt/Desktop/navigator/navigator

as the command. Right click the new shortcut, choose Permissions and choose to make it executable. Now click it and enjoy!

Want a better icon for the shortcut, right click on the shortcut and goto properties. Choose the area where the icon should be on the upper left. Click it, type this into the location, hit open:

> /home/matt/Desktop/navigator/icons

(Again, 'matt' is my user name and I have the folder on my desktop, so your path might vary)

Now pick mozicon50.xpm and hit open again. Boom, you have Netscape looking good. :)

Remember, moving the install folder will kill your shortcut. So if you need to move it, be sure to update the shortcut after. Good luck.

---

Also, it comes with a Weather extension preinstalled, tweaking help can be found here. ;)
[http://blog.insideweatherbug.com/2007/08/tweaking-weatherbug-within-new-netscape.html](http://blog.insideweatherbug.com/2007/08/tweaking-weatherbug-within-new-netscape.html)

---

