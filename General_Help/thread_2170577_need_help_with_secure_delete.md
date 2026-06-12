---
title: "need help with secure delete"
date: 2013-08-26
forum: General Help
---

### Post by Sniffingratty on 2013-08-26
hi everyone, 

I am trying to install a program to delete a drive so that the info can't ever be recovered.  I have not been able to install any .exe programs from the web, I have tried to run then with winetricks, but right clicking and saying open with Winetricks didn't do anything and opening Winetricks just gives a list of things to install without the program I downloaded and no other options.  I tired to search for WineHG (following some online advice) in software center but no results.  

So then I installed a couple of programs in Ubuntu's software center, but they didn't show up on the applications list.  I found them in the bin folder, but clicking on them does nothing.  

I know that I am a total newb, but please help me anyways.
Thanks!

---

### Post by ibjsb4 on 2013-08-26
Have you checked out DBAN?

[http://www.dban.org/](http://www.dban.org/)

---

### Post by oldos2er on 2013-08-26
> **Sniffingratty said:**
> So then I installed a couple of programs in Ubuntu's software center, but they didn't show up on the applications list.  I found them in the bin folder, but clicking on them does nothing. 

This sounds as though you installed CLI programs, which don't create a menu entry when installed, and must be run in a terminal. Knowing the names of these programs would help.

---

### Post by Sniffingratty on 2013-08-26
the programs I installed in the software center were wipe and secure-delete.

I don't understand why clicking on the executable file wouldn't run it, isn't that basically that same as runing it in a terminal.  Anyways thanks for the tips, I'll try that.

---

### Post by Sniffingratty on 2013-08-26
well I guess I need more help, i tried typing run /usr/bin/wipe  (enter); no dice and /usr/bin/wipe   (enter) nope; and dragging the file into the terminal- nope.  so how do I run the file in the terminal?  Thanks again.

---

### Post by David_Pecot on 2013-08-26
It looks like shred is an already installed shredding utility.  See here.
[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

Command line tools like "wipe" you don't run as executables.  You just invoke them from the command line.  The man page for wipe is here:
[http://lambda-diode.com/resources/wipe/wipe.1.html](http://lambda-diode.com/resources/wipe/wipe.1.html)


This also looks good, and has a GUI interface:
[http://askubuntu.com/questions/139474/gui-program-to-shred-or-wipe-files-with-options-to-make-sure-they-are-unrecovera](http://askubuntu.com/questions/139474/gui-program-to-shred-or-wipe-files-with-options-to-make-sure-they-are-unrecovera)

---

### Post by Sniffingratty on 2013-08-27
the shred utility feature looks nice in nautilus, but I don't see a systems tab anywhere.  i think ubuntu used to have a systems tab in the desktop,  maybe those instructions are for an older version?  is there a different way to get to the systems/preferences/nautilus actions configurations?  
thanks for all the help.  wish there were an easy way to do this.

---

### Post by oldos2er on 2013-08-27
> **Sniffingratty said:**
> well I guess I need more help, i tried typing run /usr/bin/wipe  (enter); no dice and /usr/bin/wipe   (enter) nope; and dragging the file into the terminal- nope.  so how do I run the file in the terminal?  Thanks again.

Can you copy & paste the terminal output from the failed command(s) here?

---

### Post by Sniffingratty on 2013-08-27
sure here is what I put in 

seth@s:~$ run /usr/hin/wipe
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (universe)
 Command 'qrun' from package 'torque-client-x11' (universe)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found
seth@s:~$ 

thanks for putting up with my newbness, hope this helps.

---

### Post by Sniffingratty on 2013-08-27
oh here we go, found a program that does a secure delete available in the software center.  installed and started up easy, easy to use with graphical interface.  perfect for a newb like me.  

unless yall think that this program is not truly secure I guess my problem is solved.  not quite as easy as a program built into nautilus and available with right click, but good enough and better than banging my head against the wall trying to figure out all this command line stuff.

---

### Post by Sniffingratty on 2013-08-27
oh yeah, it's bleach bit [https://apps.ubuntu.com/cat/applications/bleachbit/](https://apps.ubuntu.com/cat/applications/bleachbit/)

---

### Post by Sniffingratty on 2013-08-27
hmm, maybe this isn't the way to go, it says that it will take 1 days to clear my 3TB drive.  :(  are they all this slow?

---

### Post by oldos2er on 2013-08-28
> **Sniffingratty said:**
> sure here is what I put in 

seth@s:~$ run /usr/hin/wipe
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (universe)
 Command 'qrun' from package 'torque-client-x11' (universe)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found
seth@s:~$ 

thanks for putting up with my newbness, hope this helps.

Did you mean /usr/[COLOR="#FF0000"]b[/COLOR]in/wipe ? Anyway, you would need something like ```
wipe /path/file
``` where /path/file is whatever you want to delete. ```
man wipe
``` will give more details about using wipe.

---

### Post by David_Pecot on 2013-08-31
You didn't say what program it is but I'm sure it's fine ... there's several to choose from (gui and non-gui) and they all do the same thing, either secure, super-secure, or super-super-secure ... :)

---

### Post by mansonfan78 on 2013-09-01
If you go to the Ubuntu Software Center you can install "Nautilus-Actions Configuration Tool" and use it to add right-click menu items to Nautilus.  I've done this with Secure Delete.  Launch the program and go to "file" "new action".  In the "action" tab select "display item in selection context menu", enter a label and icon of your choice.  In the "command" tab, under "path" : "/usr/bin/srm" (without the quotes), "parameters": "-l %F" (copy and paste that without the quotes), "working directory": "%d" (again, no quotes).  You can ignore the rest of the tabs until "Properties" - check "enabled".  
Now go to "edit" "preferences" "runtime preferences" and uncheck "create a root nautilus-actions menu".  Close the preferences. Save and close the main program.  Now you have right-click Secure Delete in Nautilus.

---

### Post by 3rdalbum on 2013-09-01
> **Sniffingratty said:**
> hmm, maybe this isn't the way to go, it says that it will take 1 days to clear my 3TB drive.  :(  are they all this slow?

Yes, one day for a 3TB hard drive sounds right.

It's not just a case of running the computer equivalent of a Hoover across the platters. Securely wiping a hard drive involves generating random* numbers, converting them into characters and writing them to the disk until it's absolutely stuffed full. This should be repeated at least once more, but preferably twice or thrice more. The generation of these random numbers is the slow part, and three terabytes is quite a lot of random numbers!

*Computer scientists will point out that these aren't random, but "pseudo-random" or "seemingly-random". To increase the seemingly-randomness of the numbers AND the speed at which you can generate them, try and use your computer while the wiping process is happening.

---

