---
title: "configure grub menu in lubuntu?"
date: 2016-03-11
forum: General Help
---

### Post by Edison_James on 2016-03-11
Hello, I have a dual boot, lubuntu and Windows 10, I would like to change the default boot choice from line 0, which is lubuntu, to line 4 which is windows.  I have read this info. [https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2](https://help.ubuntu.com/community/Grub2/Setup#Configuring_GRUB_2)

This command 
gksu gedit /etc/default/grub &
will open a terminal, but I don't know what to do from there. I have no experience at opening a 
a configuration file with a text editor. I know which line to edit, but how to do it with root privileges
either via gksudo or from the command line, I can't figure out.

I realize this is very elementary for anyone with experience, but I would appreciate some help as it is new 
to me.  Thank you.

Edit; I have used the above link in editing the grub menu in Linux Mint as per these instructions.
The *grub* file is a system file, therefore  any editing must be done by a user with 'Administrator/root' privileges.  The file is a simple text file and can be edited by any text editor.  The default text editor in Ubuntu is Gedit, and the file can be edited  with the following command. "gksu" is the graphical equivalent of "sudo"  and the "&" allows the terminal to be used to update GRUB 2 once  the user saves the file. 

[LIST]
[*]gksu gedit /etc/default/grub &
[/LIST]
After making changes and saving the file, the GRUB 2 menu must be updated to include the changes by running: 
sudo update-grub
I seem to recall that the command opened the configuration file which I then edited and updated as per the 
instructions, but it doesn't seem to work the same with lubuntu?

---

### Post by Bob_Bruce on 2016-03-11
Looks like you're on the right track. This explains things well and helped me configure my grub menu...

[http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/](http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/)

---

### Post by yancek on 2016-03-11
I haven't used Lubuntu for a while but I believe the default text editor is leafpad so replace gedit with leafpad in your commands and preface the commands with sudo.  So do:

> sudo leafpad /etc/default/grub

that should open the file.  If windows is the fourth menuentry, you would put 3 as Grub2 counts from zero in this case.

> 
GRUB_DEFAULT=3

---

### Post by Edison_James on 2016-03-11
> **Bob_Bruce said:**
> Looks like you're on the right track. This explains things well and helped me configure my grub menu...

[http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/](http://www.howtogeek.com/196655/how-to-configure-the-grub2-boot-loaders-settings/)
  Thank you, this is a very helpful article.

---

### Post by Edison_James on 2016-03-11
> **yancek said:**
> I haven't used Lubuntu for a while but I believe the default text editor is leafpad so replace gedit with leafpad in your commands and preface the commands with sudo.  So do:



that should open the file.  If windows is the fourth menuentry, you would put 3 as Grub2 counts from zero in this case.

Thank you yancek, problem solved, changing the command from gedit to leafpad was the answer.

---

