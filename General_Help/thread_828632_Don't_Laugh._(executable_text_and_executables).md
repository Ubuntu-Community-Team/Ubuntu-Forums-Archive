---
title: "Don't Laugh. (executable text and executables)"
date: 2008-06-13
forum: General Help
---

### Post by Digital_Terror on 2008-06-13
Whenever I try to open an executable or executable text, it asks me if I should open it, then after I confirm, nothing happens. Any suggestions?[http://ubuntuforums.org/register.php?do=addmember](http://ubuntuforums.org/register.php?do=addmember)

---

### Post by tamoneya on 2008-06-13
can you be a little more detailed.  Are you trying to execute it or edit it?

if you want to execute it try one of the following:```
./executable
sudo ./executable
```

If you just want to edit try one of these:```
gedit executable
sudo gedit executable
```

---

### Post by ad_267 on 2008-06-13
Do you click on Run in Terminal, Display or Run? Do you want to execute the script or edit it?

---

### Post by Digital_Terror on 2008-06-14
I double click to run it with the GUI.

---

### Post by greenstar on 2008-06-14
If you want to Run (or execute) the script, right-click on the script and select properties, then select the Permissions tab and check the box marked Allow executing file as program.

After this, double-click on the script and select Run or Run in terminal, which one depends on the script and what you want it to do. Clicking Run will just run the script with no feedback from the terminal. If you want feedback, Run in terminal and the script will write to the terminal a log of any output messages (errors, etc.). This way you'll have a better idea of what just happened which is extremely useful to those you might ask for help.

HTH,
Greenstar

---

