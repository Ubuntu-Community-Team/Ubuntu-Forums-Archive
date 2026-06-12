---
title: "Using Wine"
date: 2005-09-21
forum: General Help
---

### Post by ubuntuubuntu on 2005-09-21
I installed a program using wine. I chose the directory "c:\program files\program_name". Where does wine copy the files? I thought they were in "/root/.wine/drive_c/program files", but it's empty. Also, I tried to use the locate  comand to find them, but I couldn't. Where are these files?
Thank you!

---

### Post by ubuntuubuntu on 2005-09-21
I have another question. When I'm using a program with Wine, it doesn't appear on the taskbar, right? So, if I go to the Desktop, how can I open the program again? Thank you.

---

### Post by cdubks88 on 2005-09-21
In response to your first question, did you install the app as your normal user?

If so, look in /home/your_user/.wine/drive_c.......yadayadayada.

The second question can be handled by creating a new custom application launcher if you wish.....right-click on the gnome panel and then select add a panel. Select Custom Application launcher. Then, if you know the actually directory of the executable, you can do it two ways: either use the winders-type path with extra backslashes, or use the unix path......

in other words, in the command field on that window you've created for the custom application launcher, it would something along the lines of:

wine /home/your-user/.wine/drive_c/Program\ Files/name_of_executable.exe

OR 

wine C:\\Program Files\\name_of_executable.exe

I'm a bit rusty with wine, so I apologize if there's errors in that syntax.....but if you look at winehq.org, the docs will lead you pretty clearly about how to call executables....then just use that syntax convention when you create your custom application launcher. 

HTH,

C.

---

### Post by ubuntuubuntu on 2005-09-22
I think you misunderstood me... What I meant is that, when I minimize a Windows application executed with Wine, it isn't shown on the bottom of the screen together with the other minimized programs. How can I open it again, then?

---

### Post by miller0521 on 2006-06-28
I am getting no answer to this question either. It seems Ubuntu is really messed up when it comes to Wine. I can use it and have it show on the taskbar in every other distro I have tried, but no go on Ubuntu, and there is nobody with an answer.

---

