---
title: "How to add website and install wordpress on ubuntu 18?"
date: 2020-02-04
forum: General Help
---

### Post by giorgi2 on 2020-02-04
Hello, i am new here and have vps hosting wit ubuntu 18. Can anyone give me a tutorial link, with help i can add website on my hosting and install wordpress?

thanks

---

### Post by TheFu on 2020-02-04
> **giorgi2 said:**
> Hello, i am new here and have vps hosting wit ubuntu 18. Can anyone give me a tutorial link, with help i can add website on my hosting and install wordpress?

thanks
Google found this: [https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview](https://ubuntu.com/tutorials/install-and-configure-wordpress#1-overview)
Searching for common questions/answers is usually the best first step.

You didn't mention a specific VPS provider.  [https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-18-04](https://www.digitalocean.com/community/tutorials/how-to-install-wordpress-with-lamp-on-ubuntu-18-04) has their tutorial.  Different VPSes will have slightly different instructions, but most will be about the same.  Many will have some sort of panel-driven installer.  If you use that, then when it is time to upgrade wordpress, hopefully, they have a good upgrade process.  

Wordpress needs to be patched almost every week, so don't expect to install and forget it.  That's how over 1,000,000 wordpress sites running today are still hacked.

If you are completely new to Unix-like OSes, be warned that there aren't point-n-click answers.  You'll need to crawl, stand, walk, before learning to job, run, sprint.  That usually takes someone about a year.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a good place to begin with beginner Linux knowledge.

---

### Post by giorgi2 on 2020-02-04
thanks

so i must add website firstly and then install apache and wordpresS?

how can it be hacked? i hosted it on good hosting provider and is their server not secured?

---

### Post by TheFu on 2020-02-04
> **giorgi2 said:**
> so i must add website firstly and then install apache and wordpresS?
Personal choice. Unimportant. Doesn't matter.....

> **giorgi2 said:**
> how can it be hacked? i hosted it on good hosting provider and is their server not secured?
That's a much bigger question with 10,000 answers, perhaps 1,000,000.  Hosting providers generally just patch the OS and only if you sign up for the $100/month plan.  The $5/month plans don't do anything.

Hacking wordpress is a popular pass time.  Start googling for how-tos and mitigations.  Also, look for best practice guides for anything you install/configure.

---

### Post by SeijiSensei on 2020-02-05
Install the "LAMP" package. This consists of Apache, MySQL and PHP, all required for WordPress.

```
sudo apt install lamp-server^
```

(the tilde is required).

Create an empty MySQL database that WordPress can use.

Next, download the latest ZIP file of WordPress from the [WP site]("https://wordpress.org/download/").  Unzip the file in /var/www/html.  You'll need to be root using sudo for this. Then change the ownership of the WP directory to the pseudo-user that Apache runs as, "www-data."

```

cd /var/www/html
sudo chown www-data:www-data wordpress -R

```

Navigate with a browser to [http://localhost/wordpress](http://localhost/wordpress).  You should be prompted for the remaining steps.

Be prepared to upgrade WP routinely whenever prompted. As TheFu says it's a constant target of hackers.  Automatic updates require that the Apache user can write into the directories where WordPress is stored. This opens you up to potential exploits. I turn off those permissions by default and re-enable them when I need to upgrade the software. I described the process here: [https://ubuntuforums.org/showthread.php?t=2430231&p=13902583&viewfull=1#post13902583](https://ubuntuforums.org/showthread.php?t=2430231&p=13902583&viewfull=1#post13902583)

---

