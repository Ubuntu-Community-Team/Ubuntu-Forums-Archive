---
title: "Launcher for an .sh file"
date: 2007-04-29
forum: General Help
---

### Post by canadianwriterman on 2007-04-29
I've installed Thinking Rock and would like to create a launcher for it. The program is executed with thinking-rock.sh and seems to only execute from within the program's directory. It won't execute from an item added to the menu or a launcher on the desktop. Any ideas? Thanks for your help

---

### Post by taurus on 2007-04-29
You need to include the whole path to where thinking-rock.sh is in your launcher.

---

### Post by krlhc8 on 2008-03-31
Right click on the the .sh file and make sure the checkbox for 
"allow execute as file" is checked in the Permissions tab.

Right click on the desktop --> Create Launcher...
In the Create Launcher menu:
Type:Application in Terminal
Name:Type in some arbitrary name here...
Command:sudo sh /home/kevin/ganttproject.sh (Just an example)
Comment:Something about the application here...

Just like taurus said, make sure the command path name is an absolute one 
like the example I used above.

I hope this helps other noobs such as myself.

---

### Post by ramjet_1953 on 2008-04-01
If you check out the attachment, you will see how to put it into your menu system

Of course, you will need to alter the path to suit your system

Just drag the icon to the box to use it in you menu.

Regards,
Roger :cool:

---

