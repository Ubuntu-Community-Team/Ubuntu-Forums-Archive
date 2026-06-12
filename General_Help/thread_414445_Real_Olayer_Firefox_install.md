---
title: "Real Olayer Firefox install"
date: 2007-04-19
forum: General Help
---

### Post by prixxie on 2007-04-19
Hello -- I'm a total Ubuntu newbie (and I love it!!)  having a very tough time trying to figure out how to install software via the terminal.  So just to start wanted to watch a trailer using RealPlayer I have to install it --- going to the Realy Player web site I download a file "RealPlayer10GOLD.bin" to my desktop.  I can see the file on the desktop but when I type in the command as in instructions below - "chmod a+x RealPlayer10GOLD.bin"  the terminal replies to me ---"chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory""

What does that mean??  Can someone please advise me on how to proceed.  Installation instructions are here below...

Go Linux!!



RealPlayer 10 for Linux is here

Installation Instructions

- Ensure that the .bin file you downloaded is executable. You can make the .bin file executable by running the "chmod a+x RealPlayer10GOLD.bin" command from a terminal window.

- Run the .bin file by typing "./RealPlayer10GOLD.bin". Follow the prompts provided to finish installing the player.

- When you launch the player for the first time, a set-up assistant will take you through configuring your player.

- Enjoy your RealPlayer10 for Linux!

---

### Post by hanzomon4 on 2007-04-20
You have to be in the right same directory as the *bin file to run YOUR command, or you can just add the path to the *.bin file like this:

The file is on your desktop, so [list=1][*]Open a terminal(command-line)


[*]Type cd to change your "current working" directory from "/home/your_username" to "/home/your_username/Desktop/" ```
cd ~/Desktop/
```

[*]Typing ls should give you a list of all the files in your "current working" directory. Look to see if the real-player *.bin file is listed```
ls
```

[*]If it's listed run your commands```
chmod a+x RealPlayer10GOLD.bin
``````
./RealPlayer10GOLD.bin
```[/list]

You may need to add "sudo" to that last command ```
sudo ./RealPlayer10GOLD.bin
``` sudo gives you superuser privileges. This may seem complicated but after a few weeks it'll make a lot more sense and be easy as pie.

---

