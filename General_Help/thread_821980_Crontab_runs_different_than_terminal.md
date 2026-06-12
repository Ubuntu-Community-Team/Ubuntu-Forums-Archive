---
title: "Crontab runs different than terminal"
date: 2008-06-07
forum: General Help
---

### Post by Pyro.699 on 2008-06-07
Hello,

I have a script. For simplicity reasons lets call it *doThis.sh*. Within this file is an extremely simple code. It changes the directory and runs the code *java main.myScript*. I need this to be run every hour on the hour; here is what my crontab looks like. *00 * * * * doThis.sh*. *doThis.sh* is located in /sbin/ (i know its not the best place to put custom scripts but its where i do). Now, i can type "doThis.sh" in the terminal window at any location and it will work fine; theres a log script that is created and everything is completed and works fine. Now, theres a block of code that ive designed that basically runs like this:
> 
Keyboard.send("Send This{Enter}");
What happens is "Send This{Enter}" is broken up into an array of individual characters. When it comes across a "{" it will add the entire value to a string creating one of the entries as "{Enter}". The array now looks like: ["S", "e"", "n", "d", " ", "T", "h", "i", "s", "{Enter}"].

A loop is then executed which examines each entry and hits that specified key on the keyboard using java.awt.*

That part really wasn't important because the script will run fine from the terminal. But when the crontab executes the log stops at the first location where there is a *Keyboard.send("Text");*. I check the process after and there is no java. So for some reason the script runs differently in crontab than it does in the terminal. I do not need root access to have it run properly (I do have it if it is required though).

Thankyou, and if you need any clarification's i would gladly provide it. This script is quite important and i need to get this done soon.

Thanks again
~Cody Woolaver

---

### Post by ibuclaw on 2008-06-07
Does the script run without an X server?

Press "**Ctrl+Alt+F1**" to switch to Virtual Terminal 1, login and run the command from there.

To switch back to X, press "**Ctrl+Alt+F7**"

Regards
Iain

---

### Post by Pyro.699 on 2008-06-07
I am going to asume not because for this script i have a shortcut made "Ctrl+Alt+Shift+t" opens a new terminal, which is required. At one point multipule tabs are opened by sending "{Alt}f" then "b".

The basic outline of the script is as follows:

Script opens up a webpage
Script gets names of posts with keywords in them
Script gets the urls of all the images in those threads
Script will place a maximum of 250 links into a single file (input[x].txt where x = an incriment number)
Script opens a new terminal window and types "wget -i input[x] [more options]" and will continue to open new tabs until it reaches the max len of x

Let me know if you need any more information

Edit:
Doing this without xserver returns the error:
**(.:30677): Gtk-WARNING **: cannot open display**

Thanks
~Cody Woolaver

---

### Post by ibuclaw on 2008-06-07
That'll be the reason why it doesn't work in crontab then Pyro.699.

Crontabs are specifically designed to handle console based low-level commands. Such as "**updatedb**" or "**apt-get update && apt-get upgrade**".
Or to put it another way, commands that don't depend on an X-server.

[EDIT]
I don't know any schedulers that run on the X-server, but you could give gnome-scheduler a try.

Regards
Iain

---

### Post by Pyro.699 on 2008-06-07
Is there any command that i could use like the one in windows. Like "cmd.exe -k <commnad>" that i could use? I looked at "bash" but couldnt get my head wraped around it. If i could open a terminal and run "doThis.sh" then it should work properly. Correct?

[edit]
I tried using gnome-schedule (its not gnome-scheduler) and from how i understand the program works is its just a user-friendly GUI for people to use. When i first opened the program it read all my current cron-jobs.

---

### Post by bingoUV on 2008-06-08
It will run fine from cron even if it requires X. Read [http://ubuntuforums.org/showthread.php?p=5068964](http://ubuntuforums.org/showthread.php?p=5068964).

Summary
1. export DISPLAY=:0.0 in cron script.
2. xhost + in your graphical terminal emulator

---

### Post by Pyro.699 on 2008-06-08
Thank you bingoUV this worked perfectly :)

---

