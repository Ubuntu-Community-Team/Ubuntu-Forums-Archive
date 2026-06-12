---
title: "Total noob question...mouse issues"
date: 2007-05-04
forum: General Help
---

### Post by Dave_57204 on 2007-05-04
Hello, I got Ubuntu 6.10 installed, however my mouse does not work, I am using a COM1 Mouse. Now I was look and I seen I have to edit a file, How do I do this like a step by step would be great, I know how to pull up the terminal in ubuntu I just don't know how to change anything any help is greatly appreciated.

Here is what I need to change for the mouse to work: 

Try changing this
Option "Device" "/dev/input/mice"
to this
Option "Device" "/dev/ttyS0"

ttyS0 = COM1 (first serial port)
ttyS1 = COM2 (second serial port)

Unless ls -l /dev/input/mice shows that it's already symbolic link to the correct device

---

### Post by Dekunuts on 2007-05-04
you have to know what the file is called you need to edit and where it can be found. You can edit it using the command line, but you can also using the GUI. 

terminal (when it says 'word', you only  type word ):
-type 'sudo' in front of a command to make it happen, as if you are administrator
-'ls' lists the contents of a directory
-'cd' changes directory as in 'cd directory' If you want to go up a level, you type 'cd ../'
-to open a file you want to change, type 'sudo gedit name_of_the_file.estension' and it will open in a normal text editor. if you change 'gedit' with 'nano' you can do everything straight from the command line

gui
-just select edit->show hidden files in nautilus and you will be able to see the system files and open them as you wish

I hope this can give you some insight in what you need to do and how things are done.

The file you probably need to edit is xorg.conf so that would be sudo gedit /etc/X11/xorg.conf

---

### Post by mikewhatever on 2007-05-04
First, backup the file
> sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

now edit what you need in the original

> gksudo gedit /etc/X11/xorg.conf

---

### Post by Dave_57204 on 2007-05-04
Still not working. I'm gonna give you all the information I had about the install and what I did, Tell me If I did something wrong. Ok, I download Ubuntu 6.10 alternate installer so I could Dual boot Linux and Windows XP from one hard drive. I procedded with the install set up the partitions and everything went fine. So I load up Ubuntu and bring up the GUI Terminal and enter the following commands (Without the quotes) : "cp /etc/x11/xorg.conf /ect/x11/xorg.conf_backup" And I got a error about directory not found or something. So I went ahead and entered "gksudo gedit /etc/x11/xorg.conf" and I got another error something about A session manger being rejected, something of that sort. So I started over again and I got the same errors. What am I doing wrong here? :confused:

---

### Post by mikewhatever on 2007-05-04
The best practice is to copy and paste the commands you enter. It was X11, not x11. For that last error you got, see here [http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)
I still do not know what that is, but it is the same in Feisty.

---

