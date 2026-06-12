---
title: "LAMP server on Non-server edition"
date: 2007-07-18
forum: General Help
---

### Post by pofigster on 2007-07-18
I installed Apache2, PHP5 and MySQL(5 i think) and dropped all of my php files into var/www - the root directory, but when I try and access them through the default address, 127.0.0.1, Apache tells me I don't have access rights to the files.

I'm running Ubuntu 6.06 in a non-root profile.  I was in root to place the files and then logged out to try and access the page.

Any ideas on why I would be getting a user permission denied and how to fix it?  Thanks!

---

### Post by az on 2007-07-18
> **pofigster said:**
> I installed Apache2, PHP5 and MySQL(5 i think) and dropped all of my php files into var/www - the root directory, but when I try and access them through the default address, 127.0.0.1, Apache tells me I don't have access rights to the files.

I'm running Ubuntu 6.06 in a non-root profile.  I was in root to place the files and then logged out to try and access the page.

Any ideas on why I would be getting a user permission denied and how to fix it?  Thanks!

Did you configure any other sites than the default?  Did you change any configurations at all?

Are the files in /var/www world-readable?

---

### Post by pofigster on 2007-07-20
Ok, I don't really know if any of the folders are world-readable or not.  I had a WAMP server running before windows up and completely failed on me.  

All I did was follow a tutorial/help page at [http://www.howtoforge.com/ubuntu_debian_lamp_server](http://www.howtoforge.com/ubuntu_debian_lamp_server)
It had me install Apache, PHP5 and MySQL (and phpmyadmin) but didn't give any other instructions on how to manage or maintain the server.  So, yes, my default directory is still var/www

Is there a way to change the root directory so it's say, on the desktop of my user account?

---

### Post by fragos on 2007-07-20
I didn't have the problems you describe but I may have installed differently than you did.  I open Synaptic, clicked the Edit menu item and selected "Mark packages by task.."  I got a popup window and checked LAMP server, closed the window and clicked the Apply icon.

---

### Post by pofigster on 2007-07-21
So do you just use /var/www then as your directory?

---

### Post by fragos on 2007-07-21
Yes.  Typing "localhost" into the browser address bar will take me there.

---

### Post by pofigster on 2007-07-22
Ok, so I did exactly as you said, I searched by function, selected LAMP server - installed.

I dropped my files into var/www using root access - and I had denied access.  So, I went and I modified the permissions of the first html file to include read-only access for everybody.  This let me see the html file - but the thing is, I have a hundreds of files (for my blog) and I don't want to have to select each of them independently of each other.

So, I guess my new question is: Is there a way to make the whole var/www folder world-readable without modifying each individual file?

Thanks!

**[COLOR="Red"]Solution:[/COLOR]**
Turns out if I just navigate to /var/www and as root enter:

find . -type f -exec chmod 644 {} \;

it'll modify all the files in the folder to user r/w everybody else r

That seems to have solved the problem!

---

### Post by fragos on 2007-07-22
Open a terminal window and do "sudo nautilus /var/www".  Now you drag any folder fom another nautilus window to /var/www and it will retain its original permissions.  All contents, even sub-folders are moved.

---

