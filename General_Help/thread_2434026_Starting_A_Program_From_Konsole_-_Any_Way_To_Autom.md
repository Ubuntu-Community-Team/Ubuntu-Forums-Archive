---
title: "Starting A Program From Konsole - Any Way To Automate It Or Create A Shortcut?"
date: 2019-12-29
forum: General Help
---

### Post by prariedog-tek on 2019-12-29
Hello--
I am new to linux (kubuntu)
I have made 2 standalone versions of my web browser. In order to run each browser I have to open it through konsole by typing this:    ./vivaldi --user-data-dir=profile &
[COLOR=#333333]
[SIZE=2]This works fine, and I am able to run 2 separate instances of my browser - but, I don't want to run the program by typing in the console everytime (if possible)
Is there a way to automate this? Maybe make a shortcut with the command already preset?
My knowledge with the konsole is very limited, so any advice is appreciated[/SIZE] [/COLOR]:confused:

---

### Post by CatKiller on 2019-12-29
> **prariedog-tek said:**
> I don't want to run the program **by typing** in the console everytime (if possible) 

Definitely don't do it like that: the command line has a history - you only need to press up/down to scroll through to previous commands. You can also have it so that you can type the first couple of letters then PageUp/PageDown to automatically search through the history for matching commands. 

Desktop files (the launchers that are used in the menu and elsewhere) are just text files with standardised entries. You can drag-and-drop one onto a text editor to see how it all works. You can make your own that does what you want. If you put it in ~/.local/share/applications it can show up in the menu, or you can have it on the desktop or whatever's convenient. 

You probably already know that the ./ part of your command means "look in *this* directory to execute this file." When you put your command in your desktop file you'll need to specify the actual path to where your file called vivaldi is.

---

### Post by prariedog-tek on 2019-12-31
Thanks for the reply - 
On the desktop I made a shortcut to the vivaldi file that runs the vivaldi.bin. I opened it in the text editor, but I can't see where I would add my text "./vivaldi --user-data-dir=profile &"

I don't know what i'm doing, so i'll ask someone for an example:
Say I have a folder on the desktop " Vivaldi", inside that folder is the executable
I want to create a shortcut to run that vivaldi with the following argument: "./vivaldi --user-data-dir=profile &"
How would I do this?

I figure going ahead and asking is more efficient than arbitrarily experimenting when I don't know what i'm doing :-\"

---

### Post by maglin2 on 2019-12-31
Not sure if this is helpful to you, but....
In my case I want to run Chromium in Kubuntu under firejail and with a cache limit size of 50MB.
I can do this as a one-off from Konsole, but for a more permanent set-up I edit the launcher (right click the Application Menu widget at left of bottom panel and select 'Edit Applications').
The KDE Menu Editor opens. I go to the Chromium entry and under Command I enter 
firejail chromium-browser --disk-cache-size=50000000
(I also then go to the Advanced tab and assign a shortcut - because that's how I like to start common applications).
Don't forget to save before you quit.

---

### Post by SeijiSensei on 2019-12-31
You could be asking one of two different things.  Do you want a way to shorten what you have to type at the command prompt? For that you can use an *alias*.

```

alias v='/path/to/vivaldi --user-data-dir=/path/to/profile &'

```

Now typing "v' will run the full command. You should use full paths in this entry (e.g, /usr/bin/vivaldi) so you can execute it from anywhere on the system.

To make this alias permanent, all this line to the bottom of the file .bashrc in your home directory. "Dot" files like this one are usually hidden, but if you open Kate then use File>Open you should be able to enter ".bashrc" in the dialog box.

If you want to customize the entry that appears in the menus, right click on the KDE icon at the left end of the Panel and choose "Edit Applications." Choose Vivaldi from the list, then modify the "command" entry to match your preferences and choose Save. (You won't need the trailing ampersand here.)

---

### Post by CatKiller on 2019-12-31
[Here's](https://ubuntuforums.org/showthread.php?t=2364670) an overview of how .desktop files work. The part that specifies the command to be run is the Exec= line. In your case you'll want to use the full path for your executable (/blah/blah/vivaldi) rather than the relative path (./vivaldi) and you won't need the trailing "&" although I don't think it would cause any harm. From your description the full path would be something like /home/prairie/Desktop/Vivaldi/vivaldi.

---

### Post by TheFu on 2019-12-31
> **prariedog-tek said:**
>  
I figure going ahead and asking is more efficient than arbitrarily experimenting when I don't know what i'm doing :-\"

More efficient 1-time, not more efficient the next 200 times for you or anyone else.

To fix the "I don't know what i'm doing" issue, start learning.  A free, no-hassle, book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)  You can buy it if you like, but I use the free PDF (in multiple languages) for reference.

Using **./program-name** is seldom used, especially by non-root users.  To learn what this really means, look up:
* relative paths, 
* absolute paths, 
* the PATH environment variable (which is used by almost every popular OS, including MS-Windows).

I cannot help with creating a my-browser-command.desktop and my-browser-command2.desktop files. I don't do stuff that way.

The great thing about almost everything in Linux is that there are 50 different solutions, each subtlety different from the others.  But if you only know 1 or 2, even when they aren't the best, most efficient, correct, ways, that is all you will use.  In the beginning, that is fine. It works. 

Eventually, you might want to setup a keyboard-chord to launch specific programs with specific options.  How that is done will be different for each GUI, DE, window manager involved and sometimes, the specific release of the core OS being used.  The post from  maglin2 goes into this a little.  I also use firejail, but sometimes I don't want any files written to disk at all when running it so I'll use 
*firejail --private  chromium-browser & * and have that launched with "<SUPER>-9".  
"<SUPER>-8" launches *firejail  chromium-browser &* which is allowed to write settings and save files to my HOME, but nowhere else. 
For trusted sites, I use firefox .... in a normal firejail - so <SUPER>-1 launches it: *firejail  firefox & *.   
Thunderbird is my thick email client.  <SUPER>-2 launches it: *firejail  thunderbird & *. 
KeepassXC is my password manager: <SUPER>-3 launches it: *firejail  keepassxc & *

You get the idea.  No menus means commonly used programs with options I prefer are quickly available.  I've created settings to launch alarms, calculators, video editors, image viewers, and a few other commonly used tools.  Even with all that, I still have .... let me count ... 9 terminal windows open for other needs.

---

### Post by prariedog-tek on 2019-12-31
Guys - i've got this saved as  vivaldi.sh on the desktop and it works:

!/bin/bash
cd '/home/sam/portable/Vivaldi/' 
./vivaldi --user-data-dir=profile &

With konsole this runs my browser in standalone mode correctly.

But clicking on the vivaldi.sh file on the desktop does nothing. Also I tried to make an entry to it in the launcher menu, when I click the shortcut, konsole pops up and reads: [COLOR=#FF5454][FONT=monospace]**Warning: Could not start program '/home/sam/Desktop/vivaldi' with arguments '/h**[/FONT][/COLOR]
[FONT=monospace]ome/sam/Desktop/vivaldi'.
[COLOR=#FF5454]**Warning: execve: Exec format error**[/COLOR]

Whats next? Thanks for all the tips btw

[/FONT]

---

### Post by TheFu on 2019-12-31
#!/bin/bash
not
!/bin/bash

BTW, the book link already provided explains this.

---

### Post by prariedog-tek on 2020-01-01
Thanks alot for the advices guys - I got it working properly. Once I understood the right way to approach it, it wasn't too hard, I didn't need any bash scripting, just a properly configured .desktop file
Thanks for taking the time to advise me.
TheFu - thanks for the book recommendation - i'll check it out
](*,)

---

