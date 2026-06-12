---
title: "Launcher Script?"
date: 2007-11-04
forum: General Help
---

### Post by Geekboy on 2007-11-04
I just finished installing the Cisco VPN Client.  I got it working fine.  I now want to create a script that will automatically open terminal and run this command:

sudo vpnclient connect (PFC Filename)

I want to create a shortcut under Applications > Internet> and call it Cisco VPN Client.

Thanks.

---

### Post by Geekboy on 2007-11-04
Any idea?

---

### Post by minus198 on 2007-11-04
System -> Preferences -> Main Menu -> Go where you wanted the starter to be -> Press: New Item -> Set "Type" to Application in terminal, add the name, and your command and if you wish, an icon. -> Press OK. And you are finished. :)

Edit: Noticed that after you have entered the sudo password, it closes.. But if that is what you want, then the above thing works.

---

### Post by Geekboy on 2007-11-04
Excellent, thanks.  That worked perfectly.  I was able to VPN into my work network.  It did keep the connection and I was able to sign on.  Thanks again.:guitar:

---

### Post by Ulrik04 on 2007-12-25
what are you going to do if you got multiple lines you want to be runned?

---

### Post by dlegend on 2007-12-25
> **Ulrik04 said:**
> what are you going to do if you got multiple lines you want to be runned?

Create a bash script file (filename.sh) with the commands you want to execute. Now just add the path to the filename.sh into the launcher and it should work.

**Creating the bash script file**
Create the filename.sh file with this line at the top:
> 
#! /bin/bash


Then every line after add your commands.

Save the file and done!

---

### Post by Ulrik04 on 2007-12-25
nice thanks :)

---

