---
title: "Unable to access phpmyadmin"
date: 2016-09-28
forum: General Help
---

### Post by david632 on 2016-09-28
Hi

I am running kubuntu 16.04.

I have spent two days on this!!  I have successfully installed LAMP and I have WordPress running on localhost.  However, I am trying to access phpmyadmin but do not seem to be having any success.  I have followed the stage 1 instructions on [https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-and-secure-phpmyadmin-on-ubuntu-16-04) . I have not gone on to stage 2.  

When I go to localhost/phpmyadmin I get this: [ATTACH=CONFIG]271381[/ATTACH]


I have tried numerous usernames including root, password, etc.  The password is the one I use for mysql database.  When clicking 'login' I get the following message: [ATTACH=CONFIG]271383[/ATTACH]

I have looked in the apache2 error log and there is this message:
"*[Wed Sep 28 12:11:15.085766 2016] [authn_file:error] [pid 18685] (2)No such file or directory: [client ::1:54406] AH01620: Could not open password file: /etc/phpmyadmin/.htpasswd*"

When looking in the folder /etc/phpmyadmin/.htpasswd (and making sure I show hidden files!) there does not seem to be a file called .htpasswd

I have researched online, looked at forums, etc.  but I cannot seem to find the solution.  Does anyone have any suggestions please?

---

### Post by spjackson on 2016-09-28
Welcome to the forums.

From reading the tutorial that you have referred to and seeing the error you are getting, I conclude that you have successfully done this bit:
```

AuthUserFile /etc/phpmyadmin/.htpasswd
```
but you have not successfully done this bit:
```

sudo htpasswd -c /etc/phpmyadmin/.htpasswd username

```
Retry this second step.

Note that the username/password that you are being prompted for is not what you may have entered in installing phpmyadmin, it is specifically what you create with the above htpasswd command.

---

### Post by david632 on 2016-09-28
Good advice and feel like I'm almost there!  Doing the above worked in that it has now taken me to the phpmyadmin.... [ATTACH=CONFIG]271385[/ATTACH]

However, I have not managed to get beyond this screen.  I have tried 'username' and the password I have set in the last step.

---

### Post by david632 on 2016-09-28
SUCCESS.... worked it out.  Did:

[COLOR=#ff9d00]sudo[/COLOR] gedit [COLOR=#ff9d00]/[/COLOR]etc[COLOR=#ff9d00]/[/COLOR]phpmyadmin[COLOR=#ff9d00]/[/COLOR]config-db.php

to find the username and password.

Really pleased and thank you for your help.  I feel like I've wasted two days but at least I've learnt a lot along the way!!  Can mark this one as solved.

---

### Post by david632 on 2016-09-28
mmm... maybe not solved!!  I am into phpmyadmin but not as root .... this seems to mean that I cannot view my WordPress database.  These are the views that I get.  The first is the login page and the second is the view I have in phpmyadmin (which seems to have reduced options, i.e. no "user accounts".

[ATTACH=CONFIG]271388[/ATTACH][ATTACH=CONFIG]271389[/ATTACH]

Can anyone advise on how to gain root access?!!

Thank you

---

### Post by spjackson on 2016-09-29
> **david632 said:**
> 
Can anyone advise on how to gain root access?!!

You would need to login as user 'root' on the 'Welcome to phpMyAdmin' page, using the root password for your mysql installation. Alternatively, if you just want access to your WordPress database, you could login using the credentials that your wordpress application uses, which will be somewhere in a wordpress settings file.

---

### Post by david632 on 2016-09-29
> **spjackson said:**
> You would need to login as user 'root' on the 'Welcome to phpMyAdmin' page, using the root password for your mysql installation. Alternatively, if you just want access to your WordPress database, you could login using the credentials that your wordpress application uses, which will be somewhere in a wordpress settings file.


Tried that and I am getting the message > [COLOR=#000000][FONT=sans-serif]#1045 - Access denied for user 'root'@'localhost' (using password: YES)[/FONT][/COLOR]

---

### Post by spjackson on 2016-10-01
> **david632 said:**
> [COLOR=#000000][FONT=sans-serif]```
#1045 - Access denied for user 'root'@'localhost' (using password: YES)
```[/FONT][/COLOR]
The most likely cause of that is that you are using the wrong password.

If you don't remember what password you used for the root account when you installed MySQL then there are many posts that tell you how to reset it e.g. [https://ubuntuforums.org/showthread.php?t=2325339](https://ubuntuforums.org/showthread.php?t=2325339)

---

