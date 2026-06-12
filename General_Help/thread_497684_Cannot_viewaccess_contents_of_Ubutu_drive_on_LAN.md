---
title: "Cannot view/access contents of Ubutu drive on LAN"
date: 2007-07-10
forum: General Help
---

### Post by MacDuff on 2007-07-10
This is SOOO frustrating. I Have installed and been testing Ubuntu (Fiesty) on two computers and am tantalizingly close to being able to replace at least one Windows system with Ubuntu but there are a couple of niggling problems still to be resolved.

Using a LAN is one of them.  Using a Windows system or second Linux/windows dual boot system, I can see the Linux machine that will hopefully become part of the network, call it "propserve".  I can use propserve to view and work with files on Windows systems with no problem, however I cannot open folders on propserve from either a windows nor another Ubuntu system.  Using windows, I get a window asking for my user name and password.  
The name and password I use when working directly on the propserve do not work.  
I created a new user and password and they do not work.

Being new to Linux and not familiar with its terminal commands, I have done everything using the Gnome interface.  I have read everything I can find about this and it appears that others have had a similar problem.  I have tried to apply the suggestions made to them without success, perhaps because the suggestions involved using terminal commands and I am missing something.

A second problem, that may be related but probably not, is that when using [System] [Adminstration] [Users & Groups] to manage users, one of the users, (me) has disappeared, leaving only the root  user displayed.  I can still log into Ubuntu and it has not impaired my ability to use the system so far as I know, but how can I display my user settings again?

Doing all this and still trying to do my regular work is starting to get me down.  How in hades do other small businesses afford to switch to Linux?  Maybe smarter people in charge of IT:confused:   Windows is starting to look like a bargain.:(

I would be grateful if someone could point me to a graphical way of allowing an inbound LAN connection.  Sorry for the long story.  It sometimes helps to unload one's frustrations.

Mac

---

### Post by stalker145 on 2007-07-10
> **MacDuff said:**
> Using a Windows system or second Linux/windows dual boot system, I can see the Linux machine that will hopefully become part of the network, call it "propserve".  I can use propserve to view and work with files on Windows systems with no problem, however I cannot open folders on propserve from either a windows nor another Ubuntu system.  Using windows, I get a window asking for my user name and password.  
The name and password I use when working directly on the propserve do not work.  
I created a new user and password and they do not work.

I'm sorry that I can't help with the second problem, but the above sounds much like an issue I was having with my server recently.

I used [this particular HowTo]("http://ubuntuforums.org/showthread.php?t=202605&highlight=howto%3Asamba") in order to get mine running properly. Pay special attention to where it tell you to put in the terminal ```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
``` as that's what it seems the main sticker is. The **-a** adds the user to Samba and the **-e** enables the user.

Check back if you continue to have problems and we'll see what can be done to get you running.

---

### Post by MacDuff on 2007-07-10
Thank you Stalker145. 

That solved my most pressing problem.  It was such a simple fix that I don't know why I could not find it myself.  The problem with learning a new system appears to be, in my case anyway, information overload.  There are so many new things to learn and subtle differences in commands and there are so many sources of information that one can get lost. 
 
Would that everything could be done with a GUI, not that I would want to deprive Linux pros from the command list.  I have been known to use them myself using different OS but when one is trying to get up to speed quickly, a GUI reduces the stress of having to read and memorize so much material.

Anyway we are another step closer to being able to dump M$ on at least two machines.

I appreciate the help provided by all of you.  Perhaps (in a year?) I will be able to contribute something in return.

Mac

---

### Post by madcow72 on 2007-07-10
You also had a question regarding a lost user account.  I have no idea why the account would have disappeared unless you accidentally deleted it, but the settings should still exist under /home/username/  I would try going to System -> Administration -> Users and Groups and then re-create your user using the *exact same* username you started with.  Gnome will automatically assign the new (old) user to its original directory where all of your configurations and settings are stored in hidden files.

Hope that works!

Oh yeah, and make sure to give yourself Administrative permissions when you create the account so that you can update and upgrade and all that.

---

### Post by MacDuff on 2007-07-10
Thanks for the reply Madcow.  I should have mentioned that I had already tried to re-create the user but I get a message that the user already exists.  So the problem is that the user exists but does not display on the "Users settings"

Does anyone know how I can get the user name and privileges  to display again?

---

