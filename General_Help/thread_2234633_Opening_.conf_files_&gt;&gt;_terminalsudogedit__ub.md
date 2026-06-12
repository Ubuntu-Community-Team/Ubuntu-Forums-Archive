---
title: "Opening .conf files &gt;&gt; terminal/sudo/gedit  ububtu 14.04/64"
date: 2014-07-15
forum: General Help
---

### Post by delanov on 2014-07-15
When using terminal to edit conf-files, I expect an conf-file to appear when I issue the command: sudo gedit conf-file.  

ddval@ddval-p6653w:~$ sudo gedit vsftpd.conf
[sudo] password for ddval:

After command executes,  A blank conf page appears titled vsftpd.conf.  It is requires the use of the drop down menu on the blank conf page to open the conf file for editing.

Also when the command is executed the following warning appears. 


[B](gedit:3666): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
[/B]

Please tell me what I'm doing wrong.

---

### Post by grahammechanical on 2014-07-15
First of all, ignore that error message. It been around for a long time. It does not stop us from doing what we what to do. You will see that error message if you opened Nautilus with administrator privileges in a terminal. It is a common event.

Second, should you not be including a path to that file you want to open? With the command that you are using Gedit is opening and creating a new file called conf-file.

Regards.

---

### Post by nerdtron on 2014-07-15
> ddval@ddval-p6653w:~$ sudo gedit vsftpd.conf

Ignore the error.
You're not not doing anything wrong but when you use gedit, provide the path of the file you want to open. In your terminal, ~$ means you are in your home folder right? This means that gedit will try to look for the vsftp on your current folder which is /home/ddval/. Since there is no file named vsftpd.conf on this folder, you'll open a blank file.

Now there are two ways to open the file you want. One is provide the complete path like this:
```
sudo gedit /etc/vsftpd.conf
```

Or you go to the directory where the file is located and then edit it, like this:
```
cd /etc/
sudo gedit vsftd.conf
```

Hope it clears up something here.

---

### Post by delanov on 2014-07-15
> **grahammechanical said:**
> First of all, ignore that error message. It been around for a long time. It does not stop us from doing what we what to do. You will see that error message if you opened Nautilus with administrator privileges in a terminal. It is a common event.

Second, should you not be including a path to that file you want to open? With the command that you are using Gedit is opening and creating a new file called conf-file.

Regards.

Thank you for your post it got me thinking and gave direction. :-)
 
a)  ddval@ddval-p6653w:~$ leafpad /etc/vsftpd.conf

 b)  ddval@ddval-p6653w:~$ sudo leafpad /etc/vsftpd.conf
     [sudo] password for ddval: 
     (leafpad:4865): IBUS-WARNING **: The owner of /home/ddval/.config/ibus/bus is not root!

 c)  ddval@ddval-p6653w:~$ gedit /etc/vsftpd.conf

 d)  ddval@ddval-p6653w:~$ sudo gedit /etc/vsftpd.conf
      [sudo] password for ddval: 


 e)  ddval@ddval-p6653w:~$ sudo -i
      root@ddval-p6653w:~# leafpad /etc/vsftpd.conf 

 f)  ddval@ddval-p6653w:~$ sudo -i
    [sudo] password for ddval: 
    root@ddval-p6653w:~# gedit /etc/vsftpd.conf

---

### Post by mc4man on 2014-07-16
There are a multitude of ways to use gedit as root, all work basically ok.
The sudo -i way you mentioned
sudo -H gedit
gksudo gedit
pkexec gedit
open directly in gedit from root file browser

The one that's a bit sketchy is sudo gedit. While that was fine prior to 13.04, from then on,  maybe not so much.
A few things stand out - 
sudo gedit uses your user config for gedit instead of root's
temporarily will take over .local/share/recently-used.xbel
may create a worthless file or 2 in your Home folder

So seems to be a poor current choice.

---

### Post by delanov on 2014-07-16
Thank you :D

---

### Post by delanov on 2014-07-16
Thank you :-)

---

### Post by delanov on 2014-07-16
> **mc4man said:**
> There are a multitude of ways to use gedit as root, all work basically ok.
The sudo -i way you mentioned
sudo -H gedit
gksudo gedit
pkexec gedit
open directly in gedit from root file browser

The one that's a bit sketchy is sudo gedit. While that was fine prior to 13.04, from then on,  maybe not so much.
A few things stand out - 
sudo gedit uses your user config for gedit instead of root's
temporarily will take over .local/share/recently-used.xbel
may create a worthless file or 2 in your Home folder

So seems to be a poor current choice.

Greatly appreciate the schooling

---

### Post by delanov on 2014-07-16
> **nerdtron said:**
> Ignore the error.
You're not not doing anything wrong but when you use gedit, provide the path of the file you want to open. In your terminal, ~$ means you are in your home folder right? This means that gedit will try to look for the vsftp on your current folder which is /home/ddval/. Since there is no file named vsftpd.conf on this folder, you'll open a blank file.

Now there are two ways to open the file you want. One is provide the complete path like this:
```
sudo gedit /etc/vsftpd.conf
```

Or you go to the directory where the file is located and then edit it, like this:
```
cd /etc/
sudo gedit vsftd.conf
```

Hope it clears up something here.

Thanks for your help.

---

### Post by delanov on 2014-07-16
> **mc4man said:**
> There are a multitude of ways to use gedit as root, all work basically ok.
The sudo -i way you mentioned
sudo -H gedit
gksudo gedit
pkexec gedit
open directly in gedit from root file browser

The one that's a bit sketchy is sudo gedit. While that was fine prior to 13.04, from then on,  maybe not so much.
A few things stand out - 
sudo gedit uses your user config for gedit instead of root's
temporarily will take over .local/share/recently-used.xbel
may create a worthless file or 2 in your Home folder

So seems to be a poor current choice.

You note: gksudo, and I've noticed others using this method.  What significance does "gk" appended to sudo serve?

---

### Post by mc4man on 2014-07-16
> **delanov said:**
> You note: gksudo, and I've noticed others using this method.  What significance does "gk" appended to sudo serve?

you can search out gksu vs sudo fairly easily, this one is pointed to often
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The answer by Vdragon  contains some useful info (not the accepted answer
[http://superuser.com/questions/202676/sudo-vs-gksudo-difference](http://superuser.com/questions/202676/sudo-vs-gksudo-difference)

---

### Post by delanov on 2014-07-17
> **mc4man said:**
> you can search out gksu vs sudo fairly easily, this one is pointed to often
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

The answer by Vdragon  contains some useful info (not the accepted answer
[http://superuser.com/questions/202676/sudo-vs-gksudo-difference](http://superuser.com/questions/202676/sudo-vs-gksudo-difference)

Thank you :-)

---

