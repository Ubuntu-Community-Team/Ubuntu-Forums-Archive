---
title: "phpwiki Installation"
date: 2005-04-19
forum: General Help
---

### Post by invalid on 2005-04-19
I attempted today to install phpwiki from the synaptic sources, but did not get too far. Here is the overview: During the installation, I was prompted for a web directory for the installation, and I left this default (/phpwiki). Looking at the terminal messages after it finished, it seems all great. However, the problem comes around now: the web directory does not exist. When I search the drive for the files, they turn up in /usr/share/phpwiki , and some config files in /etc and so on.. Anyhow, I tried to look at the documentation, but it is very minimal and not much help.

My question basically is, has anyone installed phpwiki from synaptic with success? Or if someone has a walkthrough as to how to go about setting it up so it actually works, if they could post it here.

Thanks in advance,
B.

---

### Post by jtwJGuevara on 2006-03-28
Well, this is a year late, but I stumbled upon the same problem and figured my posting will help someone else out.  To have apache2 recognize your request to http://$localhost/phpwiki, you must create a couple of entries in /etc/apache2/sites-available and /etc/apache2/sites-enabled .  Luckily, phpwiki comes with a file for this already.  Here's what you need to do:

```

sudo cp /etc/phpwiki/apache.conf /etc/apache2/sites-available/phpwiki
sudo ln /etc/apache2/sites-available/phpwiki /etc/apache2/sites-enabled/phpwiki

```

Now, after doing this I'm at the point now where I'm not longer receiving a 404 not found error, but a permissions error. Nonetheless, it solves the problem of phpwiki not being available.  Now I just have to solve the permissions problem.

**Edit:**I just solved my permission problem at least by editing /etc/apache2/sites-available/phpwiki 
```

change:
allow from 127.0.0.1

to 

allow from all

```

or change 'all' into the ip address/range you want to access phpwiki.

Cheers!

---

### Post by phoenix24x on 2007-09-14
i am a linux straggler..

i have fiesty fawn, apache2, php5, and mysql all installed 

i am attempting to get phpwiki up with no success. in your previous post i can see all the files you are referring to but i use the code i still get the 404 error

BMg

---

