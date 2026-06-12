---
title: "Radeon X700 Driver Issue"
date: 2007-03-04
forum: General Help
---

### Post by finlandia420 on 2007-03-04
Downloaded the Linux drivers from ATI's site.  When I try to run them, I get this.

> Could not open the file /home/finlandia420/Deskt…ler-8.34.8-x86.x86_64.run.

> gedit has not been able to detect the character coding.
Please check that you are not trying to open a binary file.
Select a character coding from the menu and try again.

Everything is up and running fine, just seems I am getting some graphical lag.  Thought it might be a driver issue.  Plus, was wanting to run higher than 1024X768.

---

### Post by Maestro23 on 2007-03-04
Navigate to the directory your file is in.(on your Desktop?) Then:

> cd /home/username/Desktop
sudo chmod +x filename.run
./filename.run


You can also check this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

or

Try the Envy script: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

*Works on ATI and Nvidia

---

### Post by icen64 on 2007-03-04
> **Maestro23 said:**
> 
You can also check this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)


This worked for me, =) was having a similar problem. Thank you very much =)

---

### Post by finlandia420 on 2007-03-04
Thanks for the replies, but I do not quite understand what I am to do.  The advice looks like stuff I would type in a command line.  How do I acess it.   I am new to the whole Linux thing.  I am running it graphically with a desktop, not the command line version.

*Edit* 
Figured it out.  Found the terminal.  Thanks for the help.  Lock this thread if you wish.

---

