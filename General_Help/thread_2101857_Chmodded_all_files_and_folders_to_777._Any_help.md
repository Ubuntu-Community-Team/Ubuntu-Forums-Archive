---
title: "Chmodded all files and folders to 777. Any help?"
date: 2013-01-05
forum: General Help
---

### Post by Sean Dewlin on 2013-01-05
Don't get me wrong, but this is just a pesky mistake I did while chmodding with -R flag. I wanted to set permissions only for one folder (and its contents, obviously) but suddenly realized that I'm in the root of my OS. So, yeah, now, almost all the files and folders are 777 and this is really-really bad. While making a backup of my /home folder I wanted to ask if there is any way to restore permissions? Can I install Xubuntu right over current installation - will it replace the files and correct permissions? I got quite lots of packets installed, it's not really important but I still don't want to install them all again. What can I do about this?

---

### Post by Lars Noodén on 2013-01-05
Your main option is a fresh installation.  Be sure to backup your data first.

---

### Post by Sean Dewlin on 2013-01-05
Can I install it over existing OS or I should format the whole partition? Will the installation automatically replace all the files? Thanks in advance!

---

### Post by Lars Noodén on 2013-01-05
A clean install is best.  Installing on top of an existing installation might work if it's the exact same arrangement, but no guarantees.

---

### Post by Sean Dewlin on 2013-01-05
Thank you!
```
dpkg --get-selections > installed-software
```
This does not work. Is there any other way to get the list of installed software?

---

### Post by nothingspecial on 2013-01-05
It should do.

Type ```
less installed-software
```

you should see it.

---

### Post by Sean Dewlin on 2013-01-05
This does not help a lot since I can't save the list and it's not readable by apt. Any other solution to this, sir?

---

### Post by tgalati4 on 2013-01-05
You now have a very open system.  But at least it's yours and you can change it any way you want.  Mac OS has an interesting "Repair Permissions" which can be used to both verify permission changes and the change them back to default.  Good for resetting the OS back to factory, but a pain when doing development work.

There may be a linux framework to do something similar, but I am not aware of it.

apt-cache search permissions

This brings up several tools, but you are on your own for how well they work.  Several security checkers check basic security-related files for open permissions then log them.  It would be up to you to spend several hours changing them one by one.

Clean install is in order, but first back up all of your stuff then delete /usr/bin and see how long your machine stays up.

---

### Post by Sean Dewlin on 2013-01-05
I'll see what I can do. Thanks a lot, sir! I guess the problem is solved except for the installed packages list.

---

### Post by MSPdwalt on 2013-01-05
I find it comical how often this happens.

```
pwd
``` is a great thing to do before -R lol

---

### Post by Lars Noodén on 2013-01-05
> **Sean Dewlin said:**
> Thank you!
```
dpkg --get-selections > installed-software
```
This does not work. Is there any other way to get the list of installed software?

Save the file 'installed-software' and once you have a new system do the following:

```

sudo dpkg --set-selections < installed-software
sudo apt-get dselect-upgrade

```

That will add (and remove) what you had with the old system.

---

### Post by Sean Dewlin on 2013-01-05
Wait-wait-wait, this can change the whole game. Thank you so much!

---

### Post by Lars Noodén on 2013-01-05
The > and < [redirect](http://www.linuxtopia.org/online_books/advanced_bash_scripting_guide/io-redirection.html) the output of the program to and from a file.  As nothingspecial mentioned, look in the file using [less](http://manpages.ubuntu.com/manpages/precise/en/man1/less.1.html) to see the output you saved.

If you want to review your settings without saving them, you can pipe the output into 'less'

```

dpkg --get-selections | less

```

---

### Post by Sean Dewlin on 2013-01-06
```
apt-get dselect-upgrade
```
This alone didn't work at first, so I'm writing to others who'll search for this. 
```
apt-get install dselect
```
You should install it first.
```
dselect access
```
Then, configure repositories if needed.
```
dselect update
```
Update dselect database.
```
apt-get dselect-upgrade
```
Finally run this.

---

