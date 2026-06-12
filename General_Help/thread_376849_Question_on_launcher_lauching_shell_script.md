---
title: "Question on launcher lauching shell script"
date: 2007-03-05
forum: General Help
---

### Post by gabng on 2007-03-05
Hi, I've created a shell script that starts a GUI program, along with other commands that require root access (i.e. need to input password).

The script works as intended, so I added a launcher on the toolbar to run the script.  I selected to run as "Application in console" and the script launches correctly within a terminal.

My question is is there a way to run the script so that the terminal window doesn't show up and the password input is via the GUI (i.e. like running synaptic), this is to hide it from the users, so they won't close the terminal window unintentionally before the script completes execution.  I tried to have the launcher run the script as "Application" but that didn't work.  Help is appreciated.  Thanks.

---

### Post by gabng on 2007-03-05
Anyone?

---

### Post by bestiarosa on 2007-03-29
I'd also like to know how to make some window to pop up asking for the root password when I launch admin applications via shell.
I've tried to google but haven't found a solution yet. I'm using XFCE.

Anybody out there?

---

### Post by x1a4 on 2007-03-29
Hi,

Use *zenity* and/or *gxmessage*

**Zenity**

Program that will display GTK+ dialogs, and return (either in the return code, or on standard out&#8208;put) the users input. This allows you to present information, and ask for information from the  user,  from  all manner of shell scripts.

For  example,  

*zenity  --question* 

will return either *0* or *1*, depending on whether the user pressed OK or Cancel.

*zenity --entry* 

will output on standard output what the user typed into the text entry field.

**gXmessage**

*gxmessage*  opens  a  window to display a message obtained from the command line, from a file, or from stdin. The window includes a row of buttons, each of which causes the program to exit with a different return code.

Comprehensive documentation is available in the GNOME Help Browser, under GNOME/Utilities.

System > Help > System Documentation

or just run *yelp*

---

### Post by stylishpants on 2007-03-29
Doesn't gksudo do what you want?

---

### Post by bestiarosa on 2007-03-29
> **stylishpants said:**
> Doesn't gksudo do what you want?
Yes, it was exactly what I was looking for. I didn't know gksudo worked in XFCE as well as in GNOME.

Thanks!

---

