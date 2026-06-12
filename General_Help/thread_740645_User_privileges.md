---
title: "User privileges?"
date: 2008-03-31
forum: General Help
---

### Post by jhyland87 on 2008-03-31
Hey guys, as you read my last 2 threads.. I dont want to do this without some help.. its basic..


How do I give a user root privileges? I just installed apache2, and I cant add any files to the www folder because im not root.

---

### Post by warp99 on 2008-03-31
That would be sudo <command> when using Ubuntu. More information can be found here:

[https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28sudo%29)

---

### Post by jhyland87 on 2008-03-31
Thats what I thought, but look at the attachment... I am added to admin, but I still cant edit files? I think its because I am not root, thus I cant edit roots files, just have roots permissions... how do I let 'justin' edit 'root's files?

---

### Post by warp99 on 2008-03-31
You can edit them from the command line or you can make a gksudo launcher:

[http://maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/2008/02/19](http://maketecheasier.com/ubuntu-easy-and-quick-ways-to-open-any-files-as-root/2008/02/19)

Gksudo is the graphic version of sudo. I usually just edit my files using the command line with gedit or Kate because it's easier, but everyone has a preference. 

Edit:

Let's say I wanted to edit the file 'test.php'. I would open a terminal then type 'sudo gedit /var/www/apache2-default/test.php' and the file would open in gedit with root privileges.

---

### Post by jhyland87 on 2008-03-31
I see, thats kinda what I was going for. Let me explain..

I have about 3000 files I want to move into the www folder from an external HD. I cant drag and drop due to a lack of permissions. So I can go into the terminal and use sudo I guess. Whats the command to copy files? I know windows its xcopy, but this obviously isnt windows :P (which im glad about)

---

### Post by Oldsoldier2003 on 2008-03-31
> **jhyland87 said:**
> I see, thats kinda what I was going for. Let me explain..

I have about 3000 files I want to move into the www folder from an external HD. I cant drag and drop due to a lack of permissions. So I can go into the terminal and use sudo I guess. Whats the command to copy files? I know windows its xcopy, but this obviously isnt windows :P (which im glad about)

cp is the copy command do ```
man cp
``` in a terminal for options. alternatively you can also use mv (move) again ```
man mv
``` for options.

---

### Post by warp99 on 2008-03-31
I think you need a primer on *nix and BASH (Bourne Again Shell), it's not that hard. Out of all the *nix commands there are probable five I consistently use. I have this command line reference guide printed in a binder near my computer:

[http://www.ss64.com/bash/index.html](http://www.ss64.com/bash/index.html)

and this one printed for even more information:

[http://cb.vu/unixtoolbox.xhtml](http://cb.vu/unixtoolbox.xhtml)

there is a pdf file and a booklet version available to print. Just replace the .xhtml with .pdf or .book.pdf for the booklet.

---

### Post by jhyland87 on 2008-03-31
wow, those look like they would be helpful.. thanks!

---

