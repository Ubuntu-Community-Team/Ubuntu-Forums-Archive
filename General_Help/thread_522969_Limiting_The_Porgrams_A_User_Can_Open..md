---
title: "Limiting The Porgrams A User Can Open."
date: 2007-08-11
forum: General Help
---

### Post by harley2g on 2007-08-11
Hello,

My apologizes if this question has been answered I loooked all over and did not find anything.

I am working to set up a Open Source Internet Center in Ghana ~ West Africa. We are using Dell Optiplex GX260 and are working to install Ubunto 7.04 Desktop with no Server.

As an Apple OS X user I am used to being able to limit specific functions and applications that a user has access to. Such as changing passwords, seeing other user directories, etc.

Also we only want the users to be able to access Open Office, Firefox, GIMP; along with mount a pen-drive, print.

Any adive and quidance is greatly appreciated.

Thank you,
 -h

---

### Post by deeZee on 2007-08-12
I don't know if there is a way to limit users to specific applications, but you can limit each user's privileges as follows: System>Administration>Users and Groups; select the user, go to "Properties"; then "User Privileges".  Make sure "Administer the System" is unchecked (this will prevent a user from having root or superuser privileges); also browse the other items to see if you want to place any further restrictions on your user.  Selecting "Manage Groups" will enable you to "fine tune" who has access to what.  Hope this helps! :)

---

### Post by kevinlyfellow on 2007-08-12
I have heard of this effectively being done by one of the hosts of the linux action show.  If you can't get a good answer here, you can either contact one of them or put a post up on their forum.  I've seen a few asking this question, and I really don't know the best solution to it, and I'm not sure who does.  

[http://www.linuxactionshow.com/forum/](http://www.linuxactionshow.com/forum/) 
Or download an episode and they will explain how to ask questions that will be presented on the show.

Also, once you get it figured be sure to let us know!

---

### Post by aysiu on 2007-08-12
Try Pessulus for Gnome or Kiosktool for KDE.

---

### Post by kevinlyfellow on 2007-08-14
Well, you can at least start by using lockdown features in gnome.  If you can find a way to 1) prevent the user from issuing commands 2) provide the user with launchers to the only the necessary programs you should be all set (it won't be like they won't be allowed to run a program, they just won't have a way to run that program).

That's what I remember from the podcast I listened to.  You can also make some scripts when the user log in or log out to reset any changes that they may have made.

---

### Post by harley2g on 2007-08-14
Hello and thank you everyone for the help and support.

I was able to find the podcast it is episode No. 3 for those that care to listen to it. From the decrtiption Chris and Bryan it sounds like a direct match what they had worked on..

Here is the short version..
 1. Use Alacarte Menu Editor
 2. Use the gdm (sp) login manager
 3. Use a post login session script to reset all the settings.

There are certainly a bunch of steps that are being missed in what I am writing above and I am planning to write Chris again to see if he still has the script that he used.. I am not very proficient in writing scripts.. So if anyone would like to work with me on this problem please write me so we can figure something out.

Thank you,
 H

---

### Post by kevinlyfellow on 2007-08-14
lol, I was looking for the episode recently, but I thought it was a newer one... oh well, I was only 50 or so off :-)

What I was thinking of in the post install would be to get the settings how you want them, and then back it up.  When a person logs out, the script then just removes the home folder and replaces it with the backup.  Would something like that fit your needs?  I could easily write that script, but I don't know where to actually use it.  If it needs to be included in another script that is already being run, I think I could probably be able to get that working too.

---

