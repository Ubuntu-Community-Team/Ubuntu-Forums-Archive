---
title: "I am trying to update my AVG antivirus HELP??"
date: 2008-01-30
forum: General Help
---

### Post by adn258 on 2008-01-30
But It says I don't have the proper privileges so I need to be root and that is sudo su but then what do I type to open AVG?  I tried AVG didn't work what should I do to figure this out???

---

### Post by Kilz on 2008-01-30
> **adn258 said:**
> But It says I don't have the proper privileges so I need to be root and that is sudo su but then what do I type to open AVG?  I tried AVG didn't work what should I do to figure this out???

Unless you are running a mail server, uninstall anti virus. Its not needed and the anti virus products only scan for windows viruses. None of which can effect your linux install.

---

### Post by adn258 on 2008-01-30
> **Kilz said:**
> Unless you are running a mail server, uninstall anti virus. Its not needed and the anti virus products only scan for windows viruses. None of which can effect your linux install.

no but I do a lot of stuff on msn and stuff and I may hook my computer together with my friends so I don't want them to get viruses how can I run avg in root someone help?

---

### Post by dcstar on 2008-01-30
> **adn258 said:**
> But It says I don't have the proper privileges so I need to be root and that is sudo su but then what do I type to open AVG?  I tried AVG didn't work what should I do to figure this out???

You use the exact same command that gives you the first message with "sudo" in front of it.

BTW, running an AV on a Linux box will do little (or nothing) to protect your "friends" (unless you are in the habit of downloading suspect files and deliberately sharing them), all you are doing is using up your own system resources for little gain.

---

### Post by kennedyjch on 2008-01-30
To update AVG anti-virus on my Ubuntu system I:
1) Press Alt-F2 to get command prompt
2) enter: sudo avgupdate --online
This will update the avg anti virus software online.

To scan all folders in the filesystem, I:

1) Alt-F2 to get command window
2) enter command: sudo avggui

Then I specify the folders to scan and launch the scanning session.

Using this technique I did discover a worm that crept onto a USB stick which I frequently use between my work and home.

---

### Post by Rocket2DMn on 2008-01-30
Please note that when you run graphical programs with root privileges, you should be using "gksudo" instead of normal "sudo".  See here for a little more detail - [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by Kilz on 2008-01-30
> **kennedyjch said:**
> 

Using this technique I did discover a worm that crept onto a USB stick which I frequently use between my work and home.

But since there is no such thing as a linux virus, what you found was a Windows virus, if that. Its possible you got a false positive. Unless you sent that supposedly infected file to a Windows user it does no harm. It cant propagate on a linux system.
You also point out the fact that the linux anti virus had to be manually told to scan files. It wasnt on and constantly scanning. Using up more resources to defend against the poor security of Windows, which wasnt even running.
Unless you have a mail server and send and receive mail from windows users there is no way for the virus to pass. Even if they pass it, you wouldnt, the application on the windows computer that was compromised would. But as the admin of a mail server you would want to protect the users who use your server.
Anti virus on linux is a waste of time , sold to you by the security companies that became rich as a result of the poor security of Microsoft. They use fear and misinformation to try and get people who dont need their products to get them. Most of the time sold to people with less than a year of linux use.

---

### Post by FreewheelinFrank on 2008-01-30
My AVG installation asks for my password when launching, but after that, there's no problem updating. Can't remember exactly which guide I followed. Possibly the second one will help with the update problem.

[http://ubuntuforums.org/showthread.php?t=136064](http://ubuntuforums.org/showthread.php?t=136064)


> Now when you try & update you will probably get 'cannot download avgupdate.ctf'

Go into System/administration/users & groups
Click on 'manage groups' button
Scroll right down the list to find the 'avg' group & click on it then properties button
Put a tick next to your user name.
OK/Close your way out
now LOG OUT AND BACK IN AGAIN

Update should work...

[http://ubuntuforums.org/showthread.php?t=610057](http://ubuntuforums.org/showthread.php?t=610057)

---

### Post by adn258 on 2008-01-30
> **Rocket2DMn said:**
> Please note that when you run graphical programs with root privileges, you should be using "gksudo" instead of normal "sudo".  See here for a little more detail - [http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

I want to thank everyone for all the help avggui WORKED to open AVG when I was root and from now on gksudo I will use :).  I know there are no viruses for linux really but like even windows viruses that do nothing I would prefer to kill them too lol.  Just in case they ever leak onto someone else or something.  Thanks again for all the help!!  Thank you all..

---

### Post by lisati on 2008-05-30
I had the same trouble as the OP doing an update - the solution (which I discovered from the AVG forums)is in the AVG documentation: To use the GUI-based update for AVG you need to add your Ubuntu admin user to the group AVG.

---

