---
title: "Real Player"
date: 2004-12-01
forum: General Help
---

### Post by Infatuated_iPod on 2004-12-01
I would like to install Real Player, but the instructions on the website didnt work.. 
I havent been able to install anything with The terminal in my whole life... can someone help me?

Here are the instalation instructions...

Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

---

### Post by amoser on 2004-12-01
open the terminal, go to the directory where RealPlayer was downloaded (cd [where the directory is @]).  then type chmod a+x RealPlayer10Gold.bin.  Then type sudo ./RealPlayer10Gold.bin.  When it asks you to specify where it should be installed, type /usr/lib/RealPlayer.  When the installer asks if you want to configure system-wide symbolic links hit Y. Then hit enter.  There you should be set to go.

~Alan

---

### Post by jdodson on 2004-12-01
right ok download the file or move it to your home directory.  go to a console and type:

```
ls
``` 

that command will list the contents of that directory.  make sure you see RealPlayer10GOLD.bin in the directory.  if you dont see it, it is not there or you are not finding it.

after that type in the following

```
chmod 755 ./RealPlayer10GOLD.bin
``` 

that will make it so you can execute or run the program.

after you do that type:

./RealPlayer10GOLD.bin

and you should be able to install the program.  if you are having anymore problems feel free to post them 8)

---

### Post by sebast on 2004-12-01
The first thing to know is that you need root privileges tu run the chmod command. The second is that to run those commands like that, you have to be in the same folder as your file (RealPlayer10GOLD.bin)

To know in what folder you are in the terminal type pwd. Then to go to the parent folder type cd ..

To go to a specific folder, type cd /path (ex: cd /home/user/downloads)

Then, when you are in the right folder type sudo chmod a+x RealPlayer10GOLD.bin
It will prompt for a password, type the password you use usually.

Then type ./RealPlayer10GOLD.bin

And that's it.

---

### Post by Infatuated_iPod on 2004-12-01
Copying RealPlayer files...Error creating directory /usr/lib/RealPlayer (Permission denied), exiting...
Cleaning up installation files...
Done.



I thought it was working but then this came up... 
I figured out my first problem, i didnt realize the commands were case sensitive... 
Now what do i do?

---

### Post by Infatuated_iPod on 2004-12-01
Okay, i put SUDO before the command and now everything is workin fine, thanks guys!

---

### Post by ipnjar on 2006-04-13
I can't get thebin file installed :( 

can anyone help me, i am frustrated!

this is my problem:
[FONT="Courier New"]ipnjar@ipnjar:~/Desktop$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/FONT]

---

### Post by EscapeForSurfing on 2006-04-14
[QUOTE=ipnjar]I can't get thebin file installed :( 

can anyone help me, i am frustrated!

this is my problem:
[FONT="Courier New"]ipnjar@ipnjar:~/Desktop$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory[/FONT][/QUOTE]


same problem!! 

luca@ubuntu:/home$ sudo ./RealPlayer10GOLD.bin
./RealPlayer10GOLD.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

what do you think about? btw, thanks for your tips!

EDIT: I found the problem...go to System-Admin-Synaptic and install package "libstdc++5". This will solve the problem.
Good luck!!

---

