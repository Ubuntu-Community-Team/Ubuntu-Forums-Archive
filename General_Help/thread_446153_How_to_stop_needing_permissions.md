---
title: "How to stop needing permissions"
date: 2007-05-16
forum: General Help
---

### Post by 1peter318 on 2007-05-16
[COLOR="Blue"][FONT="Comic Sans MS"]Hi, i am a new user to Linux, and choose Ubuntu 7.04 (installed last night) as i read it  it can allow me to copy from ntfs drives: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html) 

I am dual booting with Vista basic from a dell e520 with 2 sata drive an ext. enclosure. I want to copy some things to the USR folder like from my Thunderbird folder on Windows , and which i can copy from  ok, but when i try to paste them into the corresponding folder in usr/lib  it tells me i am not the owner (who else is?), and right clicking > properties>permissions is all grayed out. How can i  stop Ubuntu from always needing permissions.?  

I spend 7 years with extensive web use using  very manageable but somewhat limited W/98se,   and only (thank God) got only one virus (a minor one),  and i not  so much looking for more security, but speed and functionality.  Unlike W9x, Vista basic will not do fax and the ftp will not work, and you know what i did with the UAC! And i was able to override Vista's idea to take ownership of my files ([http://www.neowin.net/forum/index.php?showtopic=499870)](http://www.neowin.net/forum/index.php?showtopic=499870)).  So here i am with  Ubuntu with the  similar problem, and dos type commands as well.  But  by the grace of God i will learn more,  and thanks for any help you can give.  [/FONT][/COLOR]

---

### Post by orb9220 on 2007-05-16
You need to have temp root access. You achieve this thru the sudo or gksudo command.

sudo is for non graphic type commands where gksudo is for launching graphic apps like nautilus,gedit,etc..

If i create a launcher on my panel let's say home folder then right click properties for that launcher .

The command for that icon will be like > nautilus --no-desktop now if I change that command to > gksudo nautilus I will now have a full permissions browser that will give me full access.

If i open a term and **gksudo gedit /etc/X11/xorg.conf** will open that system file and give me full write permissions.

Sudo is always needed to write to a protected system file and to even install packages is run in gksudo requiring a password to install files.

For no hassle file management I have a gksudo nautilus launcher on my panel so I don't have to worry about file permissions across my partitions. But be warned you can easily bork your installation if you go messing with system files and don't know what you are doing.

Also remember you are not going to be doing everything without giving your password to do things. That is the nature of linux and security is that the system is locked down.

And it is considered annoying to use color fonts here in the forums. to make a point use bold and or quotes. But stick with the basic black text for all your posts.

---

### Post by 1peter318 on 2007-05-17
Thanks, though i am still not sure of the procedure.   Do you mean i would go to USR, and then run a terminal from Applications>Accesories and then run the script gksudo gedit /etc/X11/xorg.conf which  you offered? And how would obtain and install the gksudo nautilus launcher? Thanks.

 Sorry for the blue type; i did not know that might be objectionable.

---

### Post by orb9220 on 2007-05-17
No to copy in a gksudo nautilus. There is two ways to do it.

1) Open a term and type **gksudo nautilus** it will launch a admin browser asking for password.
now you can browse to folders and files you wish to copy. right click copy browse to where you want to copy to in this case to usr folder in root and then right click paste files or folder there.

2) Left click drag a home or computer from places onto the panel. Now there is a shortcut there. Now right click properties and under command replace the nautilus -no--desktop with **gksudo nautilus** and click ok. Now you have a admin privilege nautilus that will allow you to copy,write,delete any file.  But be careful you can do damage.

Hope this has been helpful.

> then run the script gksudo gedit /etc/X11/xorg.conf which you offered?

No this was an example to edit a text file used by the system.

---

### Post by 1peter318 on 2007-05-19
Sorry for not getting back to you sooner but thanks for the solution. I have a lot of questions, and may God bless you for offering to help

---

