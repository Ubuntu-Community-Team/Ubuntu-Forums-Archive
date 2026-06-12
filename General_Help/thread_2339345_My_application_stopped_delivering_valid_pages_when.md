---
title: "My application stopped delivering valid pages when I switched to Ubuntu 16.04"
date: 2016-10-07
forum: General Help
---

### Post by richpri on 2016-10-07
After I reinstalled Ubuntu [to upgrade to 16.04] my Apache2 local development environment stopped delivering valid pages where those pages used canvas. To illustrate, I have included two screen image files. File board18Remote.png shows a remote instance of my application where the div with the id="content" is displayed as it should be. File board18Bad.png shows the exact same code running on my local [Ubuntu 16.04] server. In it the div with the id="content" is hidden!

I have used diff to insure that the code is identical. I even tried to downgrade PHP from 7.0 back to 5.6 so it would match the remote system. but that had no effect on the problem.

The code base for my board18 application is available on github.com look for richpri/board18v2

I will be happy to supply any other information that it is within my power to supply. 
This problem has greatly impacted my ability to develop my application. I do not want to have to revert back to 14.04.

**board18Remote.png**

[http://xx.board18.org/images/board18Remote.png](http://xx.board18.org/images/board18Remote.png)

**board18Bad.png**

[http://xx.board18.org/images/board18Bad.png](http://xx.board18.org/images/board18Bad.png)

---

### Post by ajgreeny on 2016-10-07
Please do not use large images inline as you did in your post.

Please use the attachments icon, a paperclip, in the **Reply to Thread** button text-input window, or if using **Quick reply** use the Go Advanced.

---

### Post by richpri on 2016-10-09
Sorry, I will remember to avoid large images in future posts.

---

### Post by cariboo on 2016-10-11
Removed post as requested, in the future use the Report post button to ask for the mods to intervene.

---

### Post by richpri on 2016-10-12
I had created a new virtual host but I forgot to load the images to its image directory.
This caused me to make the erroneous reply that cariboo kindly removed for me. Thanks.

The interesting thing is that after I copied the images the new virtual host worked fine.
The sites-available file for the new virtual host is shown here. I also added test1.local
to my /etc/hosts file. 

```

<VirtualHost test1.local:80>
  ServerName test1.local
	ServerAdmin rich02@board18.org
	DocumentRoot /home/rich/websites/test1
    <Directory /home/rich/websites/test1/>
       Options Indexes FollowSymLinks
       AllowOverride All
       Require all granted
    </Directory>
	ErrorLog ${APACHE_LOG_DIR}/error.log
	CustomLog ${APACHE_LOG_DIR}/access.log combined
</VirtualHost>

```

I have no idea if this revised conf file solved the problem. I know for sure that the
application code was identical between the two virtual hosts and they accessed the 
same database.

I consider the issue resolved even if the root cause is still undetermined.

---

