---
title: "Edit sources.list in the Terminal?"
date: 2008-05-13
forum: General Help
---

### Post by anotherdisciple on 2008-05-13
I am helping out some friends who are new to ubuntu... I wanted to nearly automate putting things on their fresh install. How can I uncomment these lines:

```
#
## Uncomment the following two lines to add software from Canonical's
#
## 'partner' repository. This software is not part of Ubuntu, but is
#
## offered by Canonical and the respective vendors as a service to Ubuntu
#
## users.
#
# deb http://archive.canonical.com/ubuntu hardy partner
#
# deb-src http://archive.canonical.com/ubuntu hardy partner
```

from the sources.list without gedit.... Is there a way to do it in the terminal? I think there is a way to add a line to the list... some kind of echo command... I'd like to know how to do that too.

And if it's not too complicated.... how can I write a script that will just go into the terminal and do the commands for them?

Things like...

sudo aptitude remove totem totem-mozilla-plugin

sudo aptitude install ubuntu-restricted-extras exaile vlc mozilla-plugin-vlc wine


...etc


Thanks in advance


PS- I know about Automatix and stuff... but I'm not a huge fan of it... and I want to install/remove things that it doesn't do.

---

### Post by phidia on 2008-05-13
vim is a command line editor that works very well. To learn how to use it you can type vimtutor at the terminal. 

As far as writing scripts you may want to ask that as a separate question at the [programming forum]("http://ubuntuforums.org/forumdisplay.php?f=310").

---

### Post by kirios on 2008-05-13
**vi** is good but **nano** is easier. 

```
**sudo nano /etc/apt/sources.list**
```

> **anotherdisciple said:**
> How can I uncomment these lines:

```
#
## Uncomment the following two lines to add software from Canonical's
#
## 'partner' repository. This software is not part of Ubuntu, but is
#
## offered by Canonical and the respective vendors as a service to Ubuntu
#
## users.
#
# deb http://archive.canonical.com/ubuntu hardy partner
#
# deb-src http://archive.canonical.com/ubuntu hardy partner
```

from the sources.list without gedit.... Is there a way to do it in the terminal?

---

### Post by sisco311 on 2008-05-13
> **anotherdisciple said:**
> Is there a way to do it in the terminal? I think there is a way to add a line to the list... some kind of echo command... I'd like to know how to do that too.


```
sudo -s
echo -e "deb-src http://archive.canonical.com/ubuntu hardy partner\ndeb http://archive.canonical.com/ubuntu hardy partner" >> /etc/apt/sources.list
exit
```

---

### Post by unutbu on 2008-05-13
Here is a script that does some of the things you asked about. Save it to a file called 'change-sources'.

```
#!/bin/bash

cp /etc/apt/sources.list /etc/apt/sources.list-bak
cat /etc/apt/sources.list | sed -e 's|# deb http://archive.canonical.com/ubuntu hardy partner|deb http://archive.canonical.com/ubuntu hardy partner|' | sed -e 's|# deb-src http://archive.canonical.com/ubuntu hardy partner|deb-src http://archive.canonical.com/ubuntu hardy partner|' > /etc/apt/sources.list-new
echo "deb http://packages.medibuntu.org/ hardy free non-free" >> /etc/apt/sources.list-new
mv /etc/apt/sources.list-new /etc/apt/sources.list

```

Now make the file executable:
```
chmod 755 change-sources
```

You have to be root to modify /etc/apt/sources.list, so to run the script you have to use sudo:

```
sudo change-sources
```

The first command in the script saves a backup copy of your sources.list (called sources.list-bak) just in case you want to go back. 

The second command (the one that starts with 'cat') removes the pound signs (#).

The third command (the one that starts with 'echo') is an example of how to add new lines to your sources.list  from the CLI.

Since the second and third command stored their changes to sources.list-new, the fourth command moves sources.list to sources.list, so the changes will become active.

You could also make a script to install packages:

```

#!/bin/bash

aptitude remove totem totem-mozilla-plugin
aptitude install ubuntu-restricted-extras exaile vlc mozilla-plugin-vlc wine
```

As before, save it to a file, make it executable, and run it prefaced by 'sudo'.

---

### Post by anotherdisciple on 2008-05-13
Dude... you guys are awesome.... I know how to copy these ideas and do them correctly... but is there anywhere I can go to fully understand why I use things like sed -e? I want to eventually be able to do all of this without help... so I need somewhere to study this stuff.

---

### Post by unutbu on 2008-05-13
I really don't know that much about bash. I just copy down commands that I find that look useful.
Now that you have an example of how the sed -e command works, you know as much about sed as I do!

For a tutorial on sed I'd go to [http://www.grymoire.com/Unix/Sed.html](http://www.grymoire.com/Unix/Sed.html)

If you want to learn sed, you'll probably also want to learn awk: [http://www.grymoire.com/Unix/Awk.html](http://www.grymoire.com/Unix/Awk.html).

For bash in general, 
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

If you prefer having the documentation on your computer, they come in packages too:
```

sudo apt-get install bash-doc abs-guide
```

Having said that, I don't recommend learning bash first. Learn Perl. Every bash script that you might want to write can also be written in Perl, except that lots of would-be complicated things are easy in Perl and hard in bash.  

Everybody learns differently, but if you are like me and don't relish reading manuals, then I'd suggest keeping a file of useful commands. Over time you'll bump into all the commonly used stuff and before you know it you'll have all the pieces you need to write your own scripts.

Have fun!

---

### Post by bodhi.zazen on 2008-05-13
> **sisco311 said:**
> ```
sudo -s
echo -e "deb-src http://archive.canonical.com/ubuntu hardy partner\ndeb http://archive.canonical.com/ubuntu hardy partner" >> /etc/apt/sources.list
exit
```

```
sudo sh -c 'echo "deb-src http://archive.canonical.com/ubuntu hardy partner\ndeb http://archive.canonical.com/ubuntu hardy partner" >> /etc/apt/sources.list'
```

---

### Post by anotherdisciple on 2008-05-14
Is there anywhere that gives you quick definitions of sh -c...and so on instead of really long explainations? I have read a lot of material... I just want quick definitions of what each part means.

---

### Post by unutbu on 2008-05-14
Type in a terminal:

```
man sh
```

To find out what the '-c' does, type
```

/-c
```

The forward-slash (/) means 'search'. Keep typing 
```
/<RETURN>
```
to search for the next instance of -c.

Having said that, the above is not the way I actually read man pages. I like to reading man pages through emacs, which is a steep learning curve, but has the best text searching capabilities of any program I know.

---

