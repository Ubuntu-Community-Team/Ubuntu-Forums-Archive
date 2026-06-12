---
title: "Console applications don't show"
date: 2007-12-17
forum: General Help
---

### Post by Revelation60 on 2007-12-17
Hi,

I made a console application in C++ and in the Developers IDE (Code::Blocks) my console shows up perfectly. But when I try to execute my console app from the desktop no console appears. This is very user-unfriendly. Why doesn't the console show up like in Windows?


And I've got a quick second question: how can I run a file from the terminal? Just entering its name doesn't work.

---

### Post by geraldm on 2007-12-17
To bring up a terminal, press ALT + Function2 keys.  This should bring up a box.  
Enter "xterm".  That should cause the box to disappear and a new xterminal program to begin. 
In that xterm program, enter the fullpath to the executable filename.  That should start execution of the program.  
If you know the current directory that the xterm is executing in, then you can use a relative path to the executable.  The relative path to a file in the current directory begins with "./" immediately followed by the filename.

Gerald

---

### Post by Revelation60 on 2007-12-17
Thanks.

Has anyone got an answer to my first question? It is very important for me that users can just start the application without having to first start consoles and enter commands.

---

### Post by Keith Hedger on 2007-12-17
command line apps are designed to be run from a terminal or script (no gui) and dont normally open a new terminal,if you want to launch a program in a new terminal try "gnome-terminal -e top" (without the quotes) for intsance which will run the top program in a new terminal, you can put this in a executable script or a desktop file (have a look in /usr/share/applications to see some desktop files), hope this helps

---

### Post by Keith Hedger on 2007-12-17
sorry missed the second part of your question!
when you open a terminal the a path variable is loaded via your ~/.bashrc and ~/.profile so the terminal can only find commands that lie in the path (tpye  "echo $PATH" to see all the directories that the terminal will look in) if the command is not in one of these folders you will get a file not found error ,  it sounds like you are building your command but not installing it, if you use a non standard folder to store your commads you must either as geraldm said type the full path or add the path to your PATH variable ie my PATH variable in my .bashrc is set like so:
DEVPREFIX=/media/LinuxData/Development/local
PATH=${DEVPREFIX}/bin:${DEVPREFIX}/sbin:/usr/local:/usr/local/bin:"${PATH}"
you can also use ./SOMECOMMAND to run a command in the current directory

---

