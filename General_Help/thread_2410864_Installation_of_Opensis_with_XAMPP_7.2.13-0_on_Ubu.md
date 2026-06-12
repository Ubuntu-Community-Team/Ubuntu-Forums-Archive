---
title: "Installation of Opensis with XAMPP 7.2.13-0 on Ubuntu 18.04"
date: 2019-01-21
forum: General Help
---

### Post by lennoxg on 2019-01-21
I am trying to install Opensis-ce 6.0 on Ubuntu 18.04. I followed the the procedure given by [CAMAPP]("https://camapp.wordpress.com/2016/02/18/installing-opensis-on-ubuntu/")
Correction since initial post
Steps 1 to 11 were executed successfully However when i executed step 12 i got the following message given:

Job for apache2.service failed because the control process exited with error code. See "systemctl status apache2.service" and "journalctl -xe" for details.

Logs for "systemctl status apache2.service" and "journalctl -xe" are included at the bottom of the page

Before executing step 12, I verified the following MySQL Database Running ProFTPD Running Apache Web Server Running
I also verified that Xampp was setup correctly. by typing in the address bar. when i did that and pressed enter, The Xampp home page came up. i used Opera browser
[Xampps WElcome Page]("https://i.stack.imgur.com/h8YIv.png")
I also verified phpMyAdmin was installed correctly by typing:```
http://localhost/phpmyadmin
```&#8230;in the address bar and pressing enter when i did the expected page appeared
[phpmyadmin opening page]("https://i.stack.imgur.com/nv4s8.png")
i made a further observation. Using the Xampp 7.2.13-0 Graphical server manager tool. When i click on "go to applications" i get the following error message in the terminal window:
```
xdg-open: no method available for opening http://localhost:80
```
I would like to know what to do to complete the installation of Opensis-ce Thanks much
Note: i also tried using localhost port 81 and 82 instead of port 80 as some suggested without success

```
lennoxg@lennoxg-X510UAR:~$ sudo service apache2 restart
[sudo] password for lennoxg: 
Job for apache2.service failed because the control process exited with error code.
See "systemctl status apache2.service" and "journalctl -xe" for details.
lennoxg@lennoxg-X510UAR:~$ systemctl status apache2.service
&#9679; apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: failed (Result: exit-code) since Mon 2019-01-21 15:55:19 AST; 1min 38
  Process: 16706 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAIL


Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: AH00558: apache2: Could not re
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: (98)Address already in use: AH
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: (98)Address already in use: AH
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: no listening sockets available
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: AH00015: Unable to open logs
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: Action 'start' failed.
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: The Apache error log may have 
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: apache2.service: Control process exi
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: apache2.service: Failed with result 
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: Failed to start The Apache HTTP Serv
...skipping...
&#9679; apache2.service - The Apache HTTP Server
   Loaded: loaded (/lib/systemd/system/apache2.service; enabled; vendor preset: 
  Drop-In: /lib/systemd/system/apache2.service.d
           &#9492;&#9472;apache2-systemd.conf
   Active: failed (Result: exit-code) since Mon 2019-01-21 15:55:19 AST; 1min 38
  Process: 16706 ExecStart=/usr/sbin/apachectl start (code=exited, status=1/FAIL


Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: AH00558: apache2: Could not re
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: (98)Address already in use: AH
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: (98)Address already in use: AH
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: no listening sockets available
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: AH00015: Unable to open logs
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: Action 'start' failed.
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: The Apache error log may have 
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: apache2.service: Control process exi
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: apache2.service: Failed with result 
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: Failed to start The Apache HTTP Serv


lennoxg@lennoxg-X510UAR:~$ journalctl -xe
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: no listening sockets available
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: AH00015: Unable to open logs
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: Action 'start' failed.
Jan 21 15:55:19 lennoxg-X510UAR apachectl[16706]: The Apache error log may have 
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: apache2.service: Control process exi
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: apache2.service: Failed with result 
Jan 21 15:55:19 lennoxg-X510UAR systemd[1]: Failed to start The Apache HTTP Serv
-- Subject: Unit apache2.service has failed
-- Defined-By: systemd
-- Support: http://www.ubuntu.com/support
-- 
-- Unit apache2.service has failed.
-- 
-- The result is RESULT.
Jan 21 15:55:19 lennoxg-X510UAR sudo[16700]: pam_unix(sudo:session): session clo
Jan 21 15:55:20 lennoxg-X510UAR gnome-keyring-daemon[9523]: asked to register it
Jan 21 15:55:55 lennoxg-X510UAR opera_opera.desktop[10127]: [10272:10272:0121/15
Jan 21 15:57:27 lennoxg-X510UAR gnome-shell[9643]: [night-light-slider] Setting 
Jan 21 15:58:50 lennoxg-X510UAR opera_opera.desktop[10127]: [10272:10272:0121/15
Jan 21 15:59:10 lennoxg-X510UAR opera_opera.desktop[10127]: [10272:10272:0121/15
Jan 21 15:59:14 lennoxg-X510UAR opera_opera.desktop[10127]: [10272:10272:0121/15
Jan 21 15:59:43 lennoxg-X510UAR opera_opera.desktop[10127]: [10272:10272:0121/15
Jan 21 15:59:57 lennoxg-X510UAR opera_opera.desktop[10127]: [10272:10272:0121/15
lennoxg@lennoxg-X510UAR:~$
```

i am new to linux / ubuntu;  just about 5 months

---

### Post by DuckHook on 2019-01-21
Welcome to the forums, lennoxg.

Please use standard fonts and formatting when posting for ease of readability. Also, please post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by monkeybrain20122 on 2019-01-22
xampp is mainly intended for Windows users, on Linux distros it is better to set up a real LAMP, which you can do easily.

---

### Post by lennoxg on 2019-01-22
Thanks Very much DuckHook; 
Appreciate the the advice and references. will surely read them. 
Will do my best to familiarize myself with the literature

---

### Post by lennoxg on 2019-01-22
i took your advice
i uninstalled XAMPP and installed LAMP using instructions from [here]("https://howtoubuntu.org/how-to-install-lamp-on-ubuntu")
Every command executed as expected. The apache check and the php check passed; was OK
I launched the Opensis  application as instructed by placing the following Url in the address bar of my browser and pressing enter.

 [[FONT=inherit]http[/FONT][FONT=inherit]://[/FONT][FONT=inherit]localhost[/FONT][FONT=inherit]/[/FONT][FONT=inherit]opensis[/FONT][FONT=inherit]-[/FONT][FONT=inherit]ce[/FONT][FONT=inherit]/[/FONT][FONT=inherit]install[/FONT][FONT=inherit]/[/FONT][FONT=inherit]index[/FONT][FONT=inherit].[/FONT][FONT=inherit]php[/FONT]]("http://localhost/opensis-ce/install/index.php")

The application began opening up with the first three dialogue boxes shown immediately below
The application seem to freeze at the third dialogue box that was empty. 
[ATTACH=CONFIG]282276[/ATTACH][ATTACH=CONFIG]282277[/ATTACH][ATTACH=CONFIG]282278[/ATTACH]

The Opensis installation manual suggest that the display in the dialogue box immediately below  is what i should have gotten at the third dialogue box 
[ATTACH=CONFIG]282279[/ATTACH]

The dialogue box immediately below is what the Opensis Manual says i would get if my MySQL configuration is incorrect

[ATTACH=CONFIG]282280[/ATTACH]

The system displayed an empty dialogue box  at that step instead of the dialogue box with the error message
I am wondering whether the problem could still be an MySQL problem and if i have the correct port number
How can i check if the port number is correct? or if the MySQL configuration is setup correctly?
I think we are very close to resolving this
Thanks again.

---

### Post by lennoxg on 2019-03-20
This post is still open. 
I am resuming work on this problem after some time.
I uninstalled and re installed LAMP
I verified that:
[LIST]
[*]Apache is up and running 
[*]MySQL is up and running 
[*]Phpmyadmin is up and running 
[/LIST]

When i tried to setup and get opensis running, i get the message

[I]"Couldn't connect to database server: localhost 
 Possible causes are: 
 Strict mode is enabled. Please disable Strict mode and restart your mysql and apache"[/I].


The procedures i have tried used to try to disable strict mode all involve the creation of the following file:
 /etc/mysql/conf.d/disable_strict_mode.cnf

  
The problem is there is no sub directory named "mysql" under the  /etc directory on my machine. i have searched for that subdirectory several times. it  just is not there. What else can i do to disable strict mode in MySQL?

---

