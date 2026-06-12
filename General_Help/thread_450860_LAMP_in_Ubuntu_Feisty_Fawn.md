---
title: "LAMP in Ubuntu Feisty Fawn"
date: 2007-05-21
forum: General Help
---

### Post by Omkara on 2007-05-21
I installed a new clean setup of Ubuntu 7.04 (Feisty Fawn) desktop edition. Next, I installed LAMP using Synaptic. PhpMyAdmin wasn't installed, so I installed it using the terminal. That's all I did.

While using the script "BigDump", I noticed it wouldn't load properly. No errors, but also nothing shown what should be shown. 
Also, I installed a new phpBB board. The setup went fine, but the index.php won't show up and remains empty.

To test if php works, I made a phpinfo page, which is shown properly. 

What could be the problem?

---

### Post by loathsome on 2007-05-21
I'd recommend you grab the XAMPP package from [[link](http://www.apachefriends.org/en/xampp.html)] and manually set it up under /opt/lampp

That should work flawlessly.

---

### Post by Omkara on 2007-05-21
Ok I'll give it a try.

What's the best way to uninstall LAMP and mysql?
Sorry i'm kind of new at Ubuntu..

---

### Post by loathsome on 2007-05-21
Just download [this package](http://www.apachefriends.org/download.php?xampp-linux-1.6.1.tar.gz), and untar it into /opt :) Yes, it's that simple.

To start up LAMPP (included MySQL), just do a ```
sudo /opt/lampp/lampp start
```

Good luck!

---

### Post by loathsome on 2007-05-21
Ah, crap! I thought you wrote "install". If you grabbed Apache2 etc. using synaptic, you could easily do a ```
sudo apt-get remove apache2
``` in bash to remove it.

---

### Post by Omkara on 2007-05-21
Thnx a lot

I'm stunned by the fast and good help I get here :shock:

---

### Post by loathsome on 2007-05-22
No problem ;) Just glad to help.

---

### Post by az on 2007-05-22
> **Omkara said:**
> I installed a new clean setup of Ubuntu 7.04 (Feisty Fawn) desktop edition. Next, I installed LAMP using Synaptic. PhpMyAdmin wasn't installed, so I installed it using the terminal. That's all I did.

While using the script "BigDump", I noticed it wouldn't load properly. No errors, but also nothing shown what should be shown. 
Also, I installed a new phpBB board. The setup went fine, but the index.php won't show up and remains empty.

To test if php works, I made a phpinfo page, which is shown properly. 

What could be the problem?

How did you install the LAMP stack?  

I would not suggest Xampp, since you will not be able to keep up-to-date with security and bug fixes as easily.  Furthermore, unless you forgot to install a package, your problem is one with with web application you installed on top of LAMP, but not the LAMP server itself.  You will run into the same problem with Xampp.
[https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Omkara on 2007-05-22
I installed it using synaptic: Edit, select by task, and then clicked on LAMP server..

Anyhow, I removed LAMP successfully (i think), installed Xampp and everything worked perfect.. until I rebooted..
All of the sudden, I'm getting this error message when I go to my phpBB board.


General Error
SQL ERROR [ mysqli ]

Can't connect to local MySQL server through socket '/opt/lampp/var/mysql/mysql.sock' (2) [2002]

An sql error occurred while fetching this page. Please contact an administrator if this problem persists.


What could be the problem now?

---

### Post by loathsome on 2007-05-22
Clearly the MySQL-server. Did you remove the server and expect it to work? ...

---

### Post by Omkara on 2007-05-22
> **loathsome said:**
> Clearly the MySQL-server. Did you remove the server and expect it to work? ...
I obvious forgot to mention the part where I installed Xampp :D

---

### Post by loathsome on 2007-05-22
> **Omkara said:**
> I obvious forgot to mention the part where I installed Xampp :D

Aha, yes. ;) 

I recommend you set up your new MySQL application again, because the server is now located elsewhere (under /opt-something)

---

### Post by Omkara on 2007-05-22
> **loathsome said:**
> Aha, yes. ;) 

I recommend you set up your new MySQL application again, because the server is now located elsewhere (under /opt-something)
I don't see how this could be the problem.. Apache, PHP5, ... are all in the same folder ( /opt/Lampp/ ), and before the first reboot it worked perfectly.
Only after I rebooted my computer and had to restart Xampp, the problem showed up.

---

### Post by loathsome on 2007-05-22
What does the XAMPP-status show? Is MySQL "OK"?

---

### Post by Omkara on 2007-05-22
> **loathsome said:**
> What does the XAMPP-status show? Is MySQL "OK"?
It says "MySQL deactivated"
So this must be the problem..
How and where can I activate MySQL again?

---

### Post by loathsome on 2007-05-23
> **Omkara said:**
> It says "MySQL deactivated"
So this must be the problem..
How and where can I activate MySQL again?

Hi.

I have been investigating some, and I suggest you try this:
[LIST]
[*]CHMOD /opt/lampp to 777 ($ sudo chmod -R 666 /opt/lampp)
[*]Then CHMOD /opt/phpmyadmin to 765
[*]Run $ **sudo /opt/lampp/lampp restart**
[/LIST]

Please tell me how it works out for you!

---

### Post by Omkara on 2007-05-23
Eureka, everything seems to work perfect now..

Thnx a lot for the great support!!

---

### Post by got_nix on 2007-05-23
is it a definat necessity that you use xamp cuase using mysql php and apache from the repos would definatly be way easier.. install from apt-get they will be configured to work together for you.

---

### Post by loathsome on 2007-05-23
No, XAMPP *is* easier.

**Omkara**: Glad to hear that your problem got solved! :D

---

### Post by niC666 on 2007-07-16
Also, xampp provides php4 support, which is not normally available on Feisty.

I have some applications that run on PHP4 that still need to be supported, but will not be ported to PHP5.

---

### Post by marcdel on 2008-01-11
Hi all,

I've gotten lamp running previously, but I was running xamp in windows and liked the interface. I've extracted the xamp file to /opt and everything starts up fine, but when i type in my internal ip i get these log messages:

> 
Warning: file_get_contents(lang.tmp) [function.file-get-contents]: failed to open stream: Permission denied in /opt/lampp/htdocs/xampp/index.php on line 2

Warning: Cannot modify header information - headers already sent by (output started at /opt/lampp/htdocs/xampp/index.php:2) in /opt/lampp/htdocs/xampp/index.php on line 4


I tried changing the permissions, but got another warning message on line 12 of index.php (I believe). Not quite sure what the second warning is about. Any idea how to get past this?

---

