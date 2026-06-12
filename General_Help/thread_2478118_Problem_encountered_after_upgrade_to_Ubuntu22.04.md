---
title: "Problem encountered after upgrade to Ubuntu22.04"
date: 2022-08-17
forum: General Help
---

### Post by satimis on 2022-08-17
Hi all,

I have cloned WordPress websites running on an Ubuntu20.04 VM.  They can be browsed on browser running;```

http://local_ip/website_folder/

```
All of them working without problem before upgrade the VM to Ubuntu22.04.  I have checked all of them before running "Software Updater" to upgrade VM to Ubuntu22.04.

After upgrade the VM to Ubuntu22.04 on browser run;```

http://local_ip/website_folder

```
Warning:```

Your PHP installation appears to be missing the MySQL extension which is required by WordPress.

```

Please help how to fix the problem.  Thanks

Regards

---

### Post by &amp;KyT$0P# on 2022-08-17
What version of php are you using?
If the standard repo version for 22.04, do you have the [FONT=Courier New]php8.1-mysql[/FONT] package installed?

---

### Post by satimis on 2022-08-17
> **halogen2 said:**
> What version of php are you using?
If the standard repo version for 22.04, do you have the [FONT=Courier New]php8.1-mysql[/FONT] package installed?
Hi,

Thanks for your advice.

$ sudo mysql -V```

mysql  Ver 15.1 Distrib 10.6.7-MariaDB, for debian-linux-gnu (x86_64) using  EditLine wrapper

```

$ php --version```

PHP 8.1.2 (cli) (built: Jul 21 2022 12:10:37) (NTS)
Copyright (c) The PHP Group
Zend Engine v4.1.2, Copyright (c) Zend Technologies
    with Zend OPcache v8.1.2, Copyright (c), by Zend Technologies

``` 

In these 2 days I encountered lot of problem in upgrading Ubuntu20.04 to Ubuntu22.04

I wonder whether I need to continue running Ubuntu20.04 ?  Or install fresh Ubuntu22.04 on its ISO?

Regards

Regards

---

### Post by TheFu on 2022-08-17
Welcome to server administration.  

Every release changes the versions of tools we use and we have to review the release notes for the OS upgrade and each software that we are using on our servers to see what they say about version X to version Y upgrades.

That's how this has been handled for 40+ yrs.  It is part of an admin's job.  The Apache 2.2 to 2.4 migration was a bugger.  Changing php, python, perl, mysql versions, or any other server will almost always have things we need to manually change.  Over the years, I have seen a few tools (i.e. scripts) that claimed to modify X for Y upgrades, but those were usually so specialized to what the script creator needed that they never worked for anyone with a slightly different situation.  There's no magic that I'm aware.

Just because something happens to work, doesn't mean there aren't areas in the code which will break, when hit in a month.

That's life.  Sorry for the bad news.

---

### Post by satimis on 2022-08-17
> **TheFu said:**
> Welcome to server administration.  

Every release changes the versions of tools we use and we have to review the release notes for the OS upgrade and each software that we are using on our servers to see what they say about version X to version Y upgrades.

That's how this has been handled for 40+ yrs.  It is part of an admin's job.  The Apache 2.2 to 2.4 migration was a bugger.  Changing php, python, perl, mysql versions, or any other server will almost always have things we need to manually change.  Over the years, I have seen a few tools (i.e. scripts) that claimed to modify X for Y upgrades, but those were usually so specialized to what the script creator needed that they never worked for anyone with a slightly different situation.  There's no magic that I'm aware.

Just because something happens to work, doesn't mean there aren't areas in the code which will break, when hit in a month.

That's life.  Sorry for the bad news.
Thanks for your advice.

Fortunately I'm very precautionary in upgrading the OS of a VM.  First I'll clone a VM to do upgrade as testing.  Now the cloned websites on Ubuntu20.04 VM are still working and I won't do upgrade to Ubuntu22.04 on this VM.

Actually it is quite easy to build cloned websites on Ubuntu22.04 VM, just installing LAMP, importing and installing Duplicator packages, only 2, on the VM.  I'll create new cloned websites on Ubuntu22.04 VM on the new 12-cores AMD PC which I'll build at about end of this month.  But it'll take me sometime to finish creating 36 cloned websites.

Regards

---

### Post by SeijiSensei on 2022-08-18
Neither of these are the missing package. As halogen2 said, you need the php8.1-mysql package. It provides the libraries for all the mysql-specific functions in PHP.

---

### Post by satimis on 2022-08-18
> **SeijiSensei said:**
> Neither of these are the missing package. As halogen2 said, you need the php8.1-mysql package. It provides the libraries for all the mysql-specific functions in PHP.
Hi halogen2 and SeijiSensei,

Thanks for your advice.  Performed following steps on Terminal

$ sudo apt update
$ sudo apt install php8.1-mysql

reboot PC (it is needed)

I have checked all websites.

2 websites still have problem
warning```

There has been a critical error on your website.

Learn more about debugging in WordPress.

```

One website the background image missing

Regards

---

