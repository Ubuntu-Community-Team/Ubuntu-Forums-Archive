---
title: "administrator user has restricted access to files"
date: 2013-08-06
forum: General Help
---

### Post by DrScum on 2013-08-06
Using Ubuntu 12.04 LTS I constantly have problems with restricted access to certain files and folders. I am logged in with a user account listed as "administrator" but I am not able to copy anything from the home folder to, lets say /usr/share/apps in order to do that I need to start gnome commander as "administrator". 
Is this problem by design or do I have to change something in my user account?

---

### Post by newbie-user on 2013-08-06
It's not a problem. It requires elevated privileges so that you don't bork your system unknowingly, even while using an "administrator" account. If you want to be able to mess with your system without being prompted for permission, use root. Just make sure that if you use root, you know exactly what you're doing and make sure you back up all your stuff. Running rm as root is very unforgiving.

---

### Post by DrScum on 2013-08-06
Well, if I am logged in to my normal "administrator" account, have Nautilus open and want to copy a file from A to B then I might get the message "access denied". Then I either have to open Gnome Commander and start as root or I have to open Nautilus from the command line as root.

My question was: is this meant to be the case that an "administrator user" cannot copy files to lets say /usr/share/application (e.g. an application launcher for a java application) other than using the terminal or login as root.

---

### Post by bapoumba on 2013-08-06
Even in the admin group, a user wont be able to change system files without escalating first to admin privileges.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)

This is part of the security of a Linux system. Please read carefully the above links.

---

### Post by mastablasta on 2013-08-06
> **DrScum said:**
> My question was: is this meant to be the case that an "administrator user" cannot copy files to lets say /usr/share/application (e.g. an application launcher for a java application) other than using the terminal or login as root.


that is correct and as it should be. user in administrator group can temporarily become root by runnign sudo (or gksu for GUI applications). But he is not actually the admininstrator (root).

reason is not just to prevent you borking the OS. the main reson is that for the same reason user can not just change those files without passowrd that malware also needs to get your password in order to change your system files. 


after seting up the computer the root password is rarely used. mostly only for updates.

---

### Post by Mikog on 2013-08-06
The sudo command should fix your issue i think as stated above.
example copy action:

sudo cp /home/DrScum/<file-name> /usr/share/apps/

The sudo in this escalates your rights temporarily for the copy action.

---

### Post by Morbius1 on 2013-08-06
> I am logged in with a user account listed as "administrator" but I am  not able to copy anything from the home folder to, lets say  /usr/share/apps in order to do that I need to start gnome commander as  "administrator". 
Is this problem by design or do I have to change something in my user account?                 
It is by design. In fact the developers at Gnome don't even want you to use Nautilus as root ( gksu ) From the following bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=654184](https://bugzilla.gnome.org/show_bug.cgi?id=654184)
> 
You shouldn't run nautilus as root. [COLOR=#0000cd]Whats probably happening[/COLOR] here is that not
only is nautilus getting started, but also a session bus for root, and diverse 
session services, etc etc.
I find the "Whats probably happening" phrase a little disconcerting. You're the developer. You're not sure how it works?

---

### Post by DrScum on 2013-08-06
Thanks for all the replies. I do know about the sudo command I didn't know about the gksu command. These are terminal commands however and I am a complete GUI person (shame on me, I know). I was just afraid that there is something wrong with my user account. From the replies I take it that the inconveniences I was facing are the result of the safety measures built into Ubuntu and that I'll have to live with them. I guess I'll give the thread a "solved" status then.

---

### Post by bab1 on 2013-08-06
> **Morbius1 said:**
> It is by design. In fact the developers at Gnome don't even want you to use Nautilus as root ( gksu ) From the following bug report: [https://bugzilla.gnome.org/show_bug.cgi?id=654184](https://bugzilla.gnome.org/show_bug.cgi?id=654184)

The GUI uses the users home directory for configuration variables.  Using sudo or gksudo makes the user root for the session.  This means the environmental variables for root are used.  The logged in users configuration is different than the roots.  Most of the unexpected results using gksudo vs sudo usually do to these environmental variable  problems.
> 

I find the "Whats probably happening" phrase a little disconcerting. You're the developer. You're not sure how it works?

:D  More likely due to the developer not being able to confirm the specific environmental state; don't you think?  Sarcasm? 


@DrScum, From the GUI you can always open a command line for a single command using alt+cntl+f2.  A more consistent arrangement would be to assign the proper permissions and ownership of the directories you wish to store data in.  There is no reason you can't store data outside of your home directory, but you should set that up first.

---

### Post by DrScum on 2013-08-06
@bab1 I guess you meant alt+F2 since alt+ctrl+F2 would drop me to a terminal wouldn't it?

---

### Post by bab1 on 2013-08-06
> **DrScum said:**
> @bab1 I guess you meant alt+F2 since alt+ctrl+F2 would drop me to a terminal wouldn't it?
Yes you're correct.

---

### Post by newbie-user on 2013-08-06
> **DrScum said:**
> @bab1 I guess you meant alt+F2 since alt+ctrl+F2 would drop me to a terminal wouldn't it?

Actually, the ctrl+alt+t key combination will open a terminal window. Then you can "sudo su" or "sudo [command]" or "gksu" from there. No need to go to console.

---

### Post by bab1 on 2013-08-06
> **newbie-user said:**
> Actually, the ctrl+alt+t key combination will open a terminal window. Then you can "sudo su" or "sudo [command]" or "gksu" from there. No need to go to console.
I believe you have misinterpreted what I misspoke about.  ;)   

The idea was to open a single command line to execute one command.  I rarely use the GUI to open the "Run Application" dialog box and *by habit * I used the combination to open a terminal.  The console was not even in the conversation except for my misspeaking.  The OP got the drift anyway. :D

---

