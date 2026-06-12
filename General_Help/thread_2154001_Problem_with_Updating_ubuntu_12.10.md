---
title: "Problem with Updating ubuntu 12.10"
date: 2013-06-13
forum: General Help
---

### Post by babakflame on 2013-06-13
Dear Buddies
Hi
I have problem with software updater in my ubuntu (12.10).:(
This is the output of error:

[PHP]An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ir.archive.ubuntu.com_ubuntu_dists_quantal-updates_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
[/PHP]
Would some body plz hint me?

---

### Post by plucky on 2013-06-13
> Would some body plz hint me? 

From a terminal ```
sudo rm -rf /var/lib/apt/lists/*
``` will delete the list files, and then run ```
sudo apt-get update
``` to reload them.


Good Luck

---

### Post by HiImTye on 2013-06-13
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
```
sudo apt-get update
```then try again

---

### Post by babakflame on 2013-06-13
Dear Plucky
I did your codes.After typing sudo apt-get update; I got this error in the last:

```
Fetched 26.3 MB in 8min 4s (54.3 kB/s)
Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/ir.archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en
E: The package lists or status file could not be parsed or opened.
```
What should I do know?
Regards
  Bobi

---

### Post by HiImTye on 2013-06-13
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
try changing mirrors to the main server instead of your local one

---

### Post by babakflame on 2013-06-13
Dear HilmTye
Hi
I am completely unfamiliar with your sentence:
			 				
[PHP]try changing mirrors to the main server instead of your local one 				[/PHP]

Would you plz hint me?
 Regards
   Bobi

---

### Post by plucky on 2013-06-13
Open Software Sources and select **Edit > Software Sources**

On the first Tab,change the Download Server.

Good Luck

p.s You will have to run the rm command again after you have changed the server

---

### Post by babakflame on 2013-06-13
Dear Plucky When I click on Software Sources; it gives crash report and says The application Ubuntu Software Center has closed unexpectedly with these details:  Executable path: /usr/share/software-center/software-center-dbus Problem Type: crash  and some other details  what should I do?   Bobi

---

### Post by plucky on 2013-06-13
Try using Software Updater/Update Manager to access your Software Sources.

Good Luck

---

### Post by babakflame on 2013-06-13
Dear Plucky Hi  I ama bit confused. Whenever I click on updateManager; I get:  [PHP]Failed to load the package list  This is a serious problem. Try again later. If this problem appears again, please report an error to the developers. E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/ir.archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened. [/PHP]  For god's sake; what Should I dotoget rid of this counteracted loop?

---

### Post by plucky on 2013-06-13
Do you have an application called **Software & Updates** or **Software Sources** in the Dash?

Cannot remember what 12.10 used.

If so,try to open one of them.

If Software Sources opens,you can change the server there.

Or 

You could from a terminal ```
sudo rm -rf /var/lib/apt/lists/*

sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```

The second command renames the file **sources.list** to **sources.list.old**

and then go [Here](http://repogen.simplylinux.ch/) and recreate another sources.list that uses the main repository and copy it into the /etc/apt/ directory.

Good Luck

---

### Post by HiImTye on 2013-06-13
```
cp /etc/apt/sources.list /etc/apt/sources.old
sed -i -e 's|\(http[s]*://\)[a-z]*.\(.*\.ubuntu\.com\)|\1\2|' /etc/apt/sources.list
sudo apt-get update
```

---

### Post by babakflame on 2013-06-14
Dear My Friends
Hi

Practically, I got familiar with the tasks that I should do to get rid of this ridiculous problem.
At the moment, I am at this step:
[PHP]recreate another sources.list that uses the main repository and copy it into the /etc/apt/ directory.[/PHP]

I have recreated another sources.list from the ubuntu sources list generator site , But How can I copy it into /etc/apt directory? My problem is now with the following line in the site:
[PHP]Replace your /etc/apt/sources.list with the following one[/PHP]

I tried to open the sources.list.old file and copy the items from the site in it. How ever, I confronted this error:

[PHP]There is no application installed for backup file files[/PHP]

Many Thnks for your earlier kind helps and would you plz help me now?:KS

@THilmTye
Thanks for ur codes buddy, when I tried the first command I got this error:

```
babak@babak-System:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
[sudo] password for babak: 
cp: cannot stat `/etc/apt/sources.list': No such file or directory
```


Regards
  Bobi

---

### Post by plucky on 2013-06-14
> But How can I copy it into /etc/apt directory?

Edit the file with ```
gksudo gedit /etc/apt/sources.list
``` and then copy and paste the output from the source list generator into the file.Then save it.

You should now be able to run ```
sudo apt-get update
``` and see if you still get the error.

Also you might have to run the rm command to delete the broken .list file if you haven't done so before.

> I tried to open the sources.list.old file and copy the items from the site in it.

The sources.list.old file is just a backup incase you are unable to recreate a new sources.list file.

You have to now create a new **sources.list** file

Good Luck

---

### Post by HiImTye on 2013-06-14
> **babakflame said:**
> :KS@THilmTye
Thanks for ur codes buddy, when I tried the first command I got this error:

```
babak@babak-System:~$ sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
[sudo] password for babak: 
cp: cannot stat `/etc/apt/sources.list': No such file or directory
```


that's because you moved it to /etc/apt/sources.list.old

instead run
```

sudo cp /etc/apt/sources.list.old /etc/apt/sources.list
sudo sed -i -e 's|\(http[s]*://\)[a-z]*.\(.*\.ubuntu\.com\)|\1\2|' /etc/apt/sources.list
sudo apt-get update

```

[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by babakflame on 2013-06-15
Dear Buddies
Many thanks for your kind helps. It seems that the problem is solved.:KS:KS:KS

   Regards
    Bobi

---

