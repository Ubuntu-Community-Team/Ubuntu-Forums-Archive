---
title: "I cant get rainlendar to start up normally"
date: 2007-05-22
forum: General Help
---

### Post by flashsimpson on 2007-05-22
I cant get rainlendar to start up normally
I can start it with 
mike@mike-laptop:~$ sudo ~/rainlendar2/./rainlendar2

but once i close the terminal the program closes.  

my ultimate goal is to have it just start up when i boot up, but i cant seem to get it to work 
and suggestions

thanks

---

### Post by lagartoflojo on 2007-05-28
Hey!
Okay, so, to get an application to run at start-up, you have to do the following (assuming you are in Ubuntu, I don't know about Kubuntu):
Click on System -> Preferences -> Sessions
A new window will come up that has three tabs, go to the Startup Programs tab if you are not there already.
Click on the New button.
On the new window, in the Name field type "Rainlendar" (or "My calendar app" or anything else you'd like).
Now click on Next and look for the rainlendar2 executable.
Click Open.
Click OK.
Next time you log in, the calendar will be on your desktop.

... and another thing.
If you run an application from within a Terminal, the app will close when you close the Terminal. The solution for this is hitting Alt+F2 on your keyboard and typing the location of the app there (or just the name of the app if it's on your PATH).

... and something else.
I noticed that you are running rainlendar with sudo. Normally you shouldn't do this. But maybe  the app is not starting up if you don't run it with sudo. If this is the case, then do this:
Open a file browser window (Nautilus, or "Home Folder") and hit Ctrl+H on your keyboard. This will show the Hidden files.
Go to the .config/.rainlendar2 directory.
Here you will see a file called "Rainlendar2-YOURUSERNAME". Delete that file.
(This will not erase any events that you might have saved on your calendar. These are saved in the "Default.ics" file.)
Now try running rainlendar2 again, but without sudo this time. It should work.
If you find that rainlendar is not starting up again, just redo these steps (delete that file again).


Hope this helps!

---

