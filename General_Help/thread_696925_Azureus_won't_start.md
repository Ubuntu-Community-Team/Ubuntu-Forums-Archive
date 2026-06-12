---
title: "Azureus won't start"
date: 2008-02-14
forum: General Help
---

### Post by timswait on 2008-02-14
I've just installed Ubuntu 7.10 onto my new build AMD64 bit computer, I am a Linux virgin! 
I've just installed Azureus, I was setting up the options (nothing much, just changing the download directory) and it stopped responding. I clicked the close button and then "Force Quit". Now when I try and open it I get the loading screen (blue frog) then the window appears very briefly (less than a second) and instantly closes. I've tried removing the application, shutting down and restarting and reinstalling it but the same thing happens every time I open it. Any ideas what I can do? Is there some way I can remove it more thoroughly before reinstalling it? If possible I'd rather stick with the GUI, I'm not too confident using Unix and the command window.
Just found this:
[http://ubuntuforums.org/showthread.php?t=193660&highlight=azureus](http://ubuntuforums.org/showthread.php?t=193660&highlight=azureus)
I've downloaded the replacement Azureus2.jar file, but it won't let me copy it into the right folder, it says "you do not have permission to write to this folder" How do I get permission? Is this something about being the root user? This is something that annoys me about Linux, I don't need passwords or permissions on my computer, I'm the only person that uses it!

---

### Post by cozmicharlie on 2008-02-14
The permissions can be confusing and frustrating for new users but they are their for added security to protect your critical files.

What you need to do is open the folder in Nautilus as root.  Open a terminal and type or cut and paste.  
```
sudo nautilus
```
It will ask for your password - this is the password you use when you start and sign into Ubuntu.

This open Nautilus as root and now you can perform operations that require root access - just cut and paste the file Azureus2-jar file into the folder.

Also, I would recommend you install Nautilus scripts from here [http://g-scripts.sourceforge.net/](http://g-scripts.sourceforge.net/) - these scripts make life in Ubuntu much easier.  With Nautilus Scripts you can get root access by right clicking. To install.

[LIST=1]
[*]Downolad the nautilus-scripts.tar.gz file to your desktop.
[*]Right click on the downloaded folder and Extract Here.  Open the folder and there are a number of subfolders.  In the folder called "Execute" is a file called "root-nautilus-here".  You are going to copy this folder to a folder in your Home directory.
[*]Open your Home folder and in the menu go to View>Show hidden files" and open them.
[*]Go to the .gnome2>nautilus-scripts.
[*]Cut and paste the "root-nautilus-here" file into the .gnome2/nautilus-scripts folder and close.
[/LIST]
Now open any folder>right click>file>scripts and you should see "root nautilus here" - now anytime you need to root nautilus you just right click instead of having to type in a terminal and Nautilus opens as root.  Nautilus Scripts has lots of very handy scripts - read through and install any you may want just as above.

---

### Post by timswait on 2008-02-15
Thanks you for that, I've now got Azureus working. I've copied the root-nautilus-here file into the folder you say, but I don't get any scripts option when I right click a folder in the standard browser. I get the scripts>root-nautilus-here option when I've opened the window in nautilus from the terminal, but if I've just opened the window in the standard way then when I right click a folder there is no scripts menu,

---

### Post by cozmicharlie on 2008-02-15
> **timswait said:**
> Thanks you for that, I've now got Azureus working. I've copied the root-nautilus-here file into the folder you say, but I don't get any scripts option when I right click a folder in the standard browser. I get the scripts>root-nautilus-here option when I've opened the window in nautilus from the terminal, but if I've just opened the window in the standard way then when I right click a folder there is no scripts menu,

Glad to here you got Azuerus working - 1 down 1 to go!

You a sure you put the root-nautilus-here in the Home folder - Mine is 
/home/cozmicharlie/.gnome2/nautilus-scripts

Did you do this when you had Nautilus opened as root (from the terminal)? 
Do this - right click on the file you placed in the folder  and open "Properties>Permissions" and tell me who the owner is.

---

### Post by AndyCooll on 2008-02-15
> **cozmicharlie said:**
> Glad to here you got Azuerus working - 1 down 1 to go!

You a sure you put the root-nautilus-here in the Home folder - Mine is 
/home/cozmicharlie/.gnome2/nautilus-scripts

Did you do this when you had Nautilus opened as root (from the terminal)? 
Do this - right click on the file you placed in the folder  and open "Properties>Permissions" and tell me who the owner is.

Or ...you could simply install nautilus-gksu which is in the repos. Copy and paste the following into a terminal:
```
sudo apt-get install nautilus-gksu
```
It creates an "Open as administrator" entry in Nautilus's context menu.

:cool:

---

### Post by cozmicharlie on 2008-02-15
> **AndyCooll said:**
> Or ...you could simply install nautilus-gksu which is in the repos. Copy and paste the following into a terminal:
```
sudo apt-get install nautilus-gksu
```
It creates an "Open as administrator" entry in Nautilus's context menu.

:cool:

Even easier thanks for the tip.

---

### Post by timswait on 2008-02-16
Nice one, that's done the trick!

---

