---
title: "There is no file: /boot/grub/menu.lst now after a modification at grub"
date: 2014-08-27
forum: General Help
---

### Post by ruwan2 on 2014-08-27
Hi,
I have a dual boot Windows Vista/Ubuntu 12.04 LTS. This PC is a Acer compatible (AMD CPU Phenom).
I want to change the boot order to Vista as default/first. I run:

sudo su
cd /etc/grub.d/
mv 40_custom 08_custom
update-grub


from link:
[http://askubuntu.com/questions/98922/how-can-i-make-windows-boot-first-and-ubuntu-second](http://askubuntu.com/questions/98922/how-can-i-make-windows-boot-first-and-ubuntu-second)

Unfortunately, it still goes to Ubuntu first. Also, it seems that the first hard drive partition for restore Vista is shown as
Vista sda1 (? It may be different a little cause my memory does not serve that well).

Now I felt this method was not very good. I try to use the first method in above link:

gksudo gedit /boot/grub/menu.lst[COLOR=#333333][FONT=UbuntuRegular] 

But there is no menu.1st content in the editor. Now, I would reverse the above change first. Could you tell me the procedures to reverse those commands 
(mv 40_custom 08_custom etc.)?


BTW, I cannot find command to change the font background after I copy the commands to this post. Where is the button to change it to white background?

Thanks,[/FONT][/COLOR]

---

### Post by yancek on 2014-08-27
You won't be able to edit a menu.lst file as you found as it has not been available on Ubuntu for four years.  That is only on Legacy Grub and Ubuntu uses Grub2 so ignore that.  The file you want is /etc/default/grub so open that using sudo and a text editor.   Near the top of the file, you will see the line below.  What you want to do is replace the zero with the correct number.  You will need to count down to the windows menuentry you want in the boot menu or the /boot/grub/grub.cfg file.  In this instance, Grub counts from zero so if your windows is the fourth entry, you would put a number 3 below.  Save the changes and run:  sudo update-grub 

> GRUB_DEFAULT=0

---

