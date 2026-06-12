---
title: "Running Glipper on startup"
date: 2007-01-06
forum: General Help
---

### Post by gh0st on 2007-01-06
Hi folks, I am having some trouble getting Glipper to run at startup in the system tray. It runs fine if I go into Accessories and open it every time I login but when I got to Preferences -> Sessions -> Startup programs and add it, it disappears from the list as soon as I close the dialog.

My question is how do I save it so it will run at startup? There is no save button or apply button or anything like that on the dialog. I even tried ticking the checkbox that says "Automatically Save Changes To Sessions" under session options and it makes no difference. When I close the window and open it again to check the list all changes are gone.

This seems really strange :-k am I just making some newbie error here or what??

Thanks in advance for your help.

---

### Post by Asham on 2007-07-22
Did you ever get it to work?

I seem to have the same problem. I've added Glipper into the startup tab with the command 'glipper' but it wont start when I login. When I login, it's like the Glipper entry was never saved. It's no longer present in the list of applications in the startup tab. And I *did* press 'Save the current session' before I logged off! 

Edit: and when I login, it is set to use the last login session.

Any ideas? :-k

---

### Post by ahaslam on 2007-07-22
System>Preferences>Sessions>StartupPrograms>New 
Name=Glipper
Command=glipper

---

### Post by Asham on 2007-07-22
That is what I have tried but with no success. It does not start when I logon.

---

### Post by Asham on 2007-07-23
...guess I'm screwed then. :(

Can I file a bug report, and where do I do that?

---

### Post by stchman on 2007-07-23
> **gh0st said:**
> Hi folks, I am having some trouble getting Glipper to run at startup in the system tray. It runs fine if I go into Accessories and open it every time I login but when I got to Preferences -> Sessions -> Startup programs and add it, it disappears from the list as soon as I close the dialog.

My question is how do I save it so it will run at startup? There is no save button or apply button or anything like that on the dialog. I even tried ticking the checkbox that says "Automatically Save Changes To Sessions" under session options and it makes no difference. When I close the window and open it again to check the list all changes are gone.

This seems really strange :-k am I just making some newbie error here or what??

Thanks in advance for your help.

Go to a terminal and type

which glipper

It will probably come back with

/usr/bin/glipper

Try that in the Sessions manager.

---

### Post by Asham on 2007-07-23
Hi stchman,

thank you for the suggestion. I tried it and the command "which glipper" does output "/usr/bin/glipper", so I added it to the starup tab. I made sure it was in the list, closed all the dialogs and logged out. When I logged on shortly after it still wouldn't auto-launch glipper. :(

I can launch Glipper manually from the terminal, it starts up but it writes an error to the terminal window:
> asham@asham-desktop:~$ /usr/bin/glipper

(process:6815): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed
I am not sure how to interpret this message, or how to fix whatever it is that is not working properly.

- Adam

---

### Post by stchman on 2007-07-23
> **Asham said:**
> Hi stchman,

thank you for the suggestion. I tried it and the command "which glipper" does output "/usr/bin/glipper", so I added it to the starup tab. I made sure it was in the list, closed all the dialogs and logged out. When I logged on shortly after it still wouldn't auto-launch glipper. :(

I can launch Glipper manually from the terminal, it starts up but it writes an error to the terminal window:

I am not sure how to interpret this message, or how to fix whatever it is that is not working properly.

- Adam

Then it is not a Sessions startup problem.  It sounds like a glipper problem.  I have never used glipper, but the way Linux software works there is probably a ~/.glipper or something to that effect folder in your home directory.  Check to see if the folder has root only permission.  

I know that sometimes when you install KDE apps, the ~/.kde folder will be owned by root and therefore some KDE apps won't function properly.  The solution is to change ownership of the ~/.kde folder to the user logged in.

I will attempt to install glipper myself on my home system.  I will then make it startup in the Sessions manager.  I have been needing a clipboard as I Copy-Paste quite a bit.

---

### Post by Asham on 2007-07-23
Thanks for helping out. It's much appreciated.

Both the folders (.kde and .glipper) have me listed as the owner and with permissions to create and delete files.

I think that I may be on something here: I tried adding GEdit to the startup programs, but it wont startup either. :confused:

---

### Post by Asham on 2007-07-23
Yay! :popcorn:

A working fix/solution is found here: [**Sessions startup not working**]("http://ubuntuforums.org/showthread.php?t=435613&page=2").

> sudo chown -R username ~/.config
sudo chgrp -R username ~/.config
sudo chmod -R 755 ~/.config

replace username with your username

---

### Post by stchman on 2007-07-24
I have Glipper installed on two of my machines working.  I like Glipper.  Good clipboard.

---

### Post by charper_99 on 2007-08-08
> asham@asham-desktop:~$ /usr/bin/glipper

(process:6815): Gnome-CRITICAL **: gnome_program_module_register: assertion `module_info' failed

Yeah - I tried running it from the command line and I get the same thing... it doesn't seem to affect the operation though.  Aside from the 'critical' error, Glipper starts up and runs correctly from the graphical icon, the shell, and the startup programs.

---

