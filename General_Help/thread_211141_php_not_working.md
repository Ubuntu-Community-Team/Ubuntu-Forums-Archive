---
title: "php not working"
date: 2006-07-07
forum: General Help
---

### Post by nix4me on 2006-07-07
Hi,

I have installed Lamp server and everything seems to be installed correctly.  My website is working and it shows that php is installed:

Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80

The problem is, php scripts are not running.  When I click on them, they dont run and instead just pop up a handler window to open or download.

Any ideas?

nix4me

btw:  Im trying to get worpress set up per the instructions in the wiki here:[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)

---

### Post by jimmygoon on 2006-07-07
> **nix4me said:**
> Hi,

I have installed Lamp server and everything seems to be installed correctly.  My website is working and it shows that php is installed:

Apache/2.0.55 (Ubuntu) PHP/5.1.2 Server at localhost Port 80

The problem is, php scripts are not running.  When I click on them, they dont run and instead just pop up a handler window to open or download.

Any ideas?

nix4me

btw:  Im trying to get worpress set up per the instructions in the wiki here:[https://help.ubuntu.com/community/WordPress](https://help.ubuntu.com/community/WordPress)



you'll need to put them in your 'www' directory (/var/www) and access them through your browser. click one of the following, and then select the php script in there after you move them to "/var/www" (as sudo) [http://127.0.0.1](http://127.0.0.1) [http://localhost](http://localhost)

Good luck

(um I just checked out the guide and I guess it looks like you probably did that already then... so whats is currently in your "/var/www" folder?

---

### Post by nix4me on 2006-07-07
I have the wordpress working but it wont access the database now.

The wiki guide really sucks.  Its not even close to being complete.  Im totally flailing now trying to figure it out.

I have php working, but the database in not set correctly and the config file has to be edited amaong other things.  The wiki instructions arent even close.

nix4me

---

### Post by nix4me on 2006-07-08
I gave up on wordpress.  Drupal is working nicely.

nix4me

---

