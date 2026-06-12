---
title: "Firestarter startup problem"
date: 2005-07-09
forum: General Help
---

### Post by Kakistos on 2005-07-09
Whenever I login I get the following messege:-

Insufficient privileges

You must have root user privilages to use firestarter

When I initially installed firestarter, I tryed to get it to start on login by going
system - preferences - sessions - startup programs
and just adding firestarter

I had the messege come up after that.

I found a thread and followed instruction to properly get firestarter to start on login, but I still get the original error messege, and I have removed the original entry that I put in "startup programs"

Any idea how to remove the error messege.

thanks

C

---

### Post by byen on 2005-07-09
I second kakistos on this issue. the walkthrough in the thread does not work anymore... is there anyway this root-prev  message box can be fixed?
Thank you.

---

### Post by Ferio on 2005-07-10
I was about to post about this same issue, but I've found this thread before, anyone has got any idea?

---

### Post by Rincewind on 2005-07-10
[QUOTE=Kakistos]Whenever I login I get the following messege:-

Insufficient privileges

You must have root user privilages to use firestarter

When I initially installed firestarter, I tryed to get it to start on login by going
system - preferences - sessions - startup programs
and just adding firestarter

I had the messege come up after that.

I found a thread and followed instruction to properly get firestarter to start on login, but I still get the original error messege, and I have removed the original entry that I put in "startup programs"

Any idea how to remove the error messege.

thanks

C[/QUOTE]


Enter the following in a terminal:

sudo gedit /etc/sudoers

add the following text to the end (replacing username with your login):

username ALL= NOPASSWD: /etc/firestarter 



Cheers,
Rincewind (Chris  ;-) )

---

### Post by byen on 2005-07-10
[QUOTE=Rincewind]Enter the following in a terminal:

sudo gedit /etc/sudoers

add the following text to the end (replacing username with your login):

username ALL= NOPASSWD: /usr/sbin/firestarter 



Cheers,
Rincewind (Chris  ;-) )[/QUOTE]
 been there...done that... got bit again....
may be there is something I am doing wrong...checked, double checked..but cant seem to find the problem.

---

### Post by Kakistos on 2005-07-11
firestarter itself works and starts up on login.  The problem is the error messege.

C

---

### Post by Rincewind on 2005-07-11
[QUOTE=Kakistos]firestarter itself works and starts up on login.  The problem is the error messege.

C[/QUOTE]

Does the error message appear before or after you've logged into Gnome?
Is it the GUI that has the permission problems then?

Rincewind

---

### Post by Rincewind on 2005-07-11
[QUOTE=Kakistos]firestarter itself works and starts up on login.  The problem is the error messege.

C[/QUOTE]

If the error message is related to the gui starting up in Gnome, you may be trying to start the gui as a user:

Go to Sessions preferences and it should be "gksudo /etc/firestarter" in startup programs.

Rincewind

---

### Post by Rincewind on 2005-07-11
[QUOTE=byen]been there...done that... got bit again....
may be there is something I am doing wrong...checked, double checked..but cant seem to find the problem.[/QUOTE]

Oh, my mistake - I've just checked - firestarter actually resides in /etc!

OK, follow instructions as above, but using /etc/firestarter instead....


Rincewind

---

### Post by Kakistos on 2005-07-13
Error messege comes up during the GUI loading up.  

Thanks for all replys so far.  Still not solved.

C

---

### Post by arnieboy on 2005-07-13
[QUOTE=Kakistos]Error messege comes up during the GUI loading up.  

Thanks for all replys so far.  Still not solved.

C[/QUOTE]

in System-->preferences-->sessions-->startup programs add:

gksudo /usr/sbin/firestarter

This assming that u already have the "nopasswd" for sudo firestarter in ur /etc/sudoers file as was mentioned earlier in this thread. This is the correct way to do it.

---

### Post by Kakistos on 2005-07-13
Spoke to Rincewind on skype, problem solved.

in terminal type: sudo gedit /etc/sudoer

at the bottom type the following with you your username and save

yourusername ALL= NOPASSWD: /usr/sbin/firestarter

don't forget the spaces, better still cut and paste.

In sessions goto start up programs, and add the following line.

gksudo firestarter --start-hidden 

this removes the error messege, and the  --start-hidden part makes the firewall startup in the background without opening a GUI.

Thanks Rincewind

C

---

### Post by Ferio on 2005-07-14
Yeah, I knew this solution, but the point is that I want the GUI to be opened every time I log in my Ubuntu, minimized in the systray if possible. Maybe I'm asking for too much :S

---

### Post by PhilLord on 2005-07-14
I'm having the same problems. 

I've tried adding this...

system_username ALL = NOPASSWD: /usr/sbin/firestarter


to my sudoers using visudo. It all then works, until I restart, when 
sudo will always ask for a password. This happens until I run
visudo again. 

Phil

---

### Post by johhnydough on 2005-07-15
According to  the Firestarter [FAQ](http://www.fs-security.com/docs/faq.php#trayicon), adding the above mentioned line to the sudoers file ([FONT=Lucida Console]your_username ALL= NOPASSWD: /usr/sbin/firestarter[/FONT]) will get it to autostart (worked for me) and adding "[FONT=Lucida Console]sudo firestarter --start-hidden[/FONT]" to your gnome sessions startup should make firestarter startup in the notification area when you log in. 

Like I said, editing the sudoers file got it to start w/o prompting for a password when I logged in.  But I haven't tried that switch, let me know if it works.

---

### Post by arnieboy on 2005-07-15
[QUOTE=johhnydough]According to  the Firestarter [FAQ](http://www.fs-security.com/docs/faq.php#trayicon), adding the above mentioned line to the sudoers file ([FONT=Lucida Console]your_username ALL= NOPASSWD: /usr/sbin/firestarter[/FONT]) will get it to autostart (worked for me) and adding "[FONT=Lucida Console]sudo firestarter --start-hidden[/FONT]" to your gnome sessions startup should make firestarter startup in the notification area when you log in. 

Like I said, editing the sudoers file got it to start w/o prompting for a password when I logged in.  But I haven't tried that switch, let me know if it works.[/QUOTE]
a quick correction to a part of your statement: "--start-hidden" will not start start firestarter in the notification area. It will result in firestarter working w/o any icon anywhere which is not nice since u dont know whats happening. It would be good if they add an option in a future version to start firestarter in the notification area without opening up the main window every time I log in and make me use alt-F4 to close it.

---

### Post by crispingatiesa on 2005-07-15
The option --start-hidden shows firestarter in the notification area, at least in my machine. 

U have to have the notification area visible though. I know that because I made it dissapear once! 

Shamefully I don't have access to my ubuntu box now so, I cannot check what I did. If later this has not being solve I'll post how I manage to make it work.

---

### Post by arnieboy on 2005-07-15
[QUOTE=crispingatiesa]The option --start-hidden shows firestarter in the notification area, at least in my machine. 

U have to have the notification area visible though. I know that because I made it dissapear once! 

Shamefully I don't have access to my ubuntu box now so, I cannot check what I did. If later this has not being solve I'll post how I manage to make it work.[/QUOTE]

the last time I tried it, the icon did not show up in the notification area.. but u may be right.. i will give it a try again when i go back home today.

---

### Post by Ferio on 2005-07-16
Yeah, it happens to me, too.

---

### Post by stig on 2005-07-16
[QUOTE=Kakistos]Spoke to Rincewind on skype, problem solved.

in terminal type: sudo gedit /etc/sudoer

at the bottom type the following with you your username and save

yourusername ALL= NOPASSWD: /usr/sbin/firestarter

C[/QUOTE]

I'm trying to follow this and do the NOPASSWD in sudoer but when I type "sudo gedit /etc/sudoer" in terminal I get a file called etc/sudoer but it is blank.

If I try the Ubuntu advice and use visudo in terminal I get the sudoers file and can add the NOPASSWD line - but how do I save and close? If I press Esc and type the advised :wq it just appears as text in the file. Yet my Esc key works OK elsewhere.

---

### Post by arunsub on 2005-07-22
What's the equivalent of this command in KDE?
gksudo firestarter --start-hidden

---

### Post by amrust on 2005-08-05
This problem is happening to me too.

Ubuntu booted normally yesterday, started doing this today.

After booting into GNOME, I get the "insufficient privleges" dialog.

I *do* have the line following line in my /etc/sudoers: (with my *actual* username)

```
yourusername ALL= NOPASSWD: /usr/sbin/firestarter
``` 

and I have the following line in my System -> Preferences -> Sessions -> Startup Programs section:

```
sudo firestarter --start-hidden 
``` 

Then firestarter appears running in my notification bar at the top of the screen. Firestarter seems to be running as it always did, but for some reason I now get a VERY ANNOYING error dialog, instead of the clean-booting Ubuntu I was just starting to get comfortable with. Can anyone PLEASE refer me to a way to fix this?

---

### Post by amrust on 2005-08-05
Also, I have noticed that when trying to launch Firestarter from the Applications -> System Tools menu, it launches 2 Firestarters. When I check behind the launcher, it is apparently running the line

gksudo /usr/sbin/firestarter

instead of the proper

sudo /usr/sbin/firestarter


Why would this start happening all of a sudden? Things worked fine yesterday.  :mad: 

I hate to do it, but I am switching to Windows on dual boot, until (assuming) I am able to get this resolved. I like a clean and stable user interface. I had one yesterday, for some reason Ubuntu has decided to stop working properly.  I do not like booting up Ubuntu, and seeing an error message like "Insufficient privleges", when it worked fine the day before. I have followed all steps in the guide and the Firestarter FAQ. I have uninstalled and reinstalled Firestarter. 

Someone PLEASE help me before I do the unthinkable and switch back to my crappy XP. :(

---

### Post by arnieboy on 2005-08-05
[QUOTE=amrust]This problem is happening to me too.

Ubuntu booted normally yesterday, started doing this today.

After booting into GNOME, I get the "insufficient privleges" dialog.

I *do* have the line following line in my /etc/sudoers: (with my *actual* username)

```
yourusername ALL= NOPASSWD: /usr/sbin/firestarter
``` 

and I have the following line in my System -> Preferences -> Sessions -> Startup Programs section:

```
sudo firestarter --start-hidden 
``` 

Then firestarter appears running in my notification bar at the top of the screen. Firestarter seems to be running as it always did, but for some reason I now get a VERY ANNOYING error dialog, instead of the clean-booting Ubuntu I was just starting to get comfortable with. Can anyone PLEASE refer me to a way to fix this?[/QUOTE]

in System --> Preferences --> Sessions --> Startup Programs change "sudo firestarter --start-hidden" to
"gksudo firestarter --start-hidden"
that should solve ur problem.

---

### Post by amrust on 2005-08-05
Tried changing "sudo firestarter --start-hidden" to
"gksudo firestarter --start-hidden".....

That stopped Firestarter from launching completely. Still got that blasted "Insufficient privleges" dialog, too. :mad: I thought gksudo was for KDE and sudo was for GNOME. I run GNOME.

That brings me to the 2nd point of weirdness.... when I launch Firestarter from the Applications -> System Tools menu, it appears to launch 2 seperate instances of Firestarter. it used to behave normally. Has something changed to make some of these programs mistakenly think I am running KDE instead of GNOME?

Reason I say, is because if I add Firestarter to my panel, and right-click check Preferences, it lists it is trying to launch 'gksudo /usr/sbin/firestarter'

Changing the launcher to 'sudo /usr/sbin/firestarter' allows it to start normally.

The ONLY thing I have done out of the ordinary lately, is when I logged out yesterday, I selected "save current setup". Would that have screwed something up in my desktop, or sessions, or Firestarter?

Edit: resolved, i edited /etc/sudoers with sudo visudo.

---

### Post by Ferio on 2005-10-14
I've just upgraded to Breezy Badger, and now the problem is different: it asks for the password, but then it disappears and spends 2 or 3 minutes until Firestarter is loaded, though I'm not sure about it, 'cos the last time it seemed to load when I pressed the return key. Any idea?

---

### Post by Nordoelum on 2006-04-02
Hope this will fix the problem :D

---

### Post by Death_Sargent on 2007-03-19
All of those fixes made it so only root could launch the thing

---

