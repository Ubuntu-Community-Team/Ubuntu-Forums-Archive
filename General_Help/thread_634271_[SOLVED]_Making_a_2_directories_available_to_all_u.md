---
title: "[SOLVED] Making a 2 directories available to all users"
date: 2007-12-07
forum: General Help
---

### Post by vsiege on 2007-12-07
Problem: I would like to have a 2 "link to..." in users /home folder. At present time I can only write to my own /home/me and cannot figure out how to have two central points where each user can save to. I have two HDs and would like each user to have access to both. I can reinstall the OS if that makes life easier to achieve this.

My setup:
2X 500 gig HDDs
first drive:
[INDENT]use as: ext 3 journeling file system
mount point: /
mount options: defaults
label: none
reserved blocks: 5 %
typical usage: standard
bootable flag: none[/INDENT]
*appears as File System on my desktop*
second drive:
[INDENT]use as: ext 3 journeling file system
mount point: /media/best
mount options: defaults
label: none
reserved blocks: 5 %
typical usage: standard
bootable flag: none[/INDENT]
*appears as 500G Volume on my desktop*

---

### Post by derby007 on 2007-12-07
A re-install shouldn't be necessary.
Try this, (note: I'm typing this off the top of my head, ahem) : If you can read/write to the 2nd harddrive, then you can have other users do the same. Create a new group, add the users to the new group, create a folder on 2nd drive, change group ownership of the folder to the new group. Create links in their /home folder to the new folder.

---

### Post by vsiege on 2007-12-07
thanx. I have doen this so far.
Made a folder on HD 2 and shared it to a group [read/write] and put a link in my user home folder.

PROBLEMS: 
1. it will not let me alter the contents of any other users i created.... that is the contents of their /home/diffUser/ folder or any other part of the first drive so that i can put links in their to thw two save. locations

2. also how do i get a directory on the first drive thats common. the idea is... if the drive fails... i have data on both HDs.

BTW i have Xfce installed on top of U.Server 7.10 with SAMBA and more

---

### Post by derby007 on 2007-12-07
Only 'root' can alter other peoples /home contents, try 'sudo'  in a terminal before any commands, or I like to open a 'root terminal'. You get this option in the MENU editor under 'System Tools' link. or in a terminal: type: 'sudo nautilus'. BE CAREFUL with 'root' commands.

---

### Post by vsiege on 2007-12-07
Two things...
where do i put the dirctory on the first drive? /mnt or /media or something else?

Using the sudo commands...Ive used them to install apps...im in xubuntu and root terminal isnt in the place you described.....plus the CLI cmd did not work

I notice when a user creates a folder or a file in the new share... the group has [read] access... can you force all new files and folders in a certain directory to have a certain group that read/write?

guess i had more than jjus two things! thanks

I am going to reinstall ( had lost mysql password and cant get into phpmyadmin) & thinking maybe i will go with gnome deskptop on top of the server 7.10... i imagine theres a way to trim it down later.. most of the tutorials are for ubuntu... i dont know either one all that well and really wanted to try to configure LAMP, SFTP and SAMBA in xfce. mainly b/c of how small it is too run.  I still want to give it a try before i reinstall though, jus attacking bits and pieces in my spare time

---

### Post by derby007 on 2007-12-08
> where do i put the dirctory on the first drive? /mnt or /media or something else? 
>> I think you can put it anywhere, /tmp/xxx  is probably a good place.

> im in xubuntu and root terminal isnt in the place you described.....plus the CLI cmd did not work
>> Sorry, I forgot u were in XFCE, to use a "root" terminal, type "sudo -i" at the command line. 'gksudo thunar' or 'nautilus' if u have that package.
'RootTerminal' > But I think it still might be in the MenuEditor, but then again I'm running Gnome & XFCE.
Or create a link/shortcut on taskbar with command: "gksudo x-terminal-emulator -geometry 80x24+10+10" (if I remember rightly)  :)

> can you force all new files and folders in a certain directory to have a certain group that read/write?

>> I presume it can be done, not sure off the top of my head.

> had lost mysql password and cant get into phpmyadmin
>> You can recover MySQL database server password with following five easy steps.

Step # 1: Stop the MySQL server process.
# /etc/init.d/mysql stop

Step # 2: Start the MySQL (mysqld) server/daemon process with the &#8211;skip-grant-tables option so that it will not prompt for password
# mysqld_safe --skip-grant-tables &

Step # 3: Connect to mysql server as the root user
# mysql -u root

Step # 4: Setup new root password
mysql> use mysql;
mysql> update user set password=PASSWORD("NEW-ROOT-PASSWORD") where User='root';
mysql> flush privileges;
mysql> quit

Step # 5: Exit and restart MySQL server
# /etc/init.d/mysql stop

Start MYSQL & test it:
# /etc/init.d/mysql start
# mysql -u root -p

---

### Post by vsiege on 2007-12-08
:-D Thank you so much. I marked the thread as answered.


For future reference is there any one source the describes the function of directories such as /tmp, /media, /mnt and so on? Or is this eomthing you just pick up along the way?

---

