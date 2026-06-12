---
title: "How to add repository?"
date: 2008-06-01
forum: General Help
---

### Post by Paulo M. on 2008-06-01
Hello everyone!
(sorry for double posting this question, but in repository partner forum I got no help at all...)
Please, I need some help: I'm still a newbie in ubuntu, and I want to install an application I found in CVS at sourceforge.net (stylus toolbox 1.1) but I have 2 problems... In first place I don't know how to add (if needed) that repository ([http://stylus-toolbox.cvs.sourceforg...lus%20Toolbox/](http://stylus-toolbox.cvs.sourceforg...lus%20Toolbox/)) and either don't know how to install that application (I've already installed cvs in synaptic)
Can, anyone, please tell me how to?

Thanks in advance!

---

### Post by ibuclaw on 2008-06-01
Open up a terminal and make a src directory in your account.
```
mkdir ~/src
```
Then cd into it:
```
cd ~/src
```
Now with CVS, the sourcecode has to be downloaded and compiled by yourself.

To acquire the source. Copy and paste this into the terminal:
```
cvs -z3 -d:pserver:anonymous@stylus-toolbox.cvs.sourceforge.net:/cvsroot/stylus-toolbox co -P stylus-toolbox
```
And then cd into the newly created directory
```
cd stylus-toolbox
```

Then compile the source using make.

Regards
Iain

---

### Post by Paulo M. on 2008-06-01
Thank you very, very, very much!
Really... I thought that it would be easier... (that compile the source using make stuff... I don't know if I an able to do it!)
I'll give it a try anyway... and soon I'll be back here and post the results!

All my best!

---

### Post by ibuclaw on 2008-06-01
> **Paulo M. said:**
> Thank you very, very, very much!
Really... I thought that it would be easier... (that compile the source using make stuff... I don't know if I an able to do it!)
I'll give it a try anyway... and soon I'll be back here and post the results!

All my best!

Type in ```
sudo make install
```

Iain

---

### Post by Paulo M. on 2008-06-01
Hello again, and thank you very much one more time...
I made all of it and seems I didn't mess anything :)
But tell me one more thing, please... with this procedure, is the application already installed? It seems to me that now I need to install it, but, I don't really know how...

All my best (...)

---

### Post by ibuclaw on 2008-06-01
If you typed in **sudo make install** and entered your password correctly, then it is installed.

To run it (just reading the setup.py file)... Looks like all you have to do is just type in **stylus-toolbox** and it will run.

Regards
Iain

---

### Post by Paulo M. on 2008-06-01
again......... thanks!
Yes I did type it just like that and entered password correctly as well....
But in file ~/src/stylus-toolbox/README I can see:

"Installation
============

To install, edit the Makefile as appropriate and then do a `make install' as
root.

Usage
=====

Before you run, due to a known issue in the configuration file handling code, 
you need to do a `touch ~/.stylus-toolbox.conf'  (FITNR)

Also, you either need to have read-write access to the raw printer device
(something like /dev/lp0 or /dev/usblp0), or you need to run as root."

Maybe thats why I can't run the application!

---

### Post by ibuclaw on 2008-06-01
Ah. Good eyes Paulo.

```
touch ~/.stylus-toolbox.conf
```

And as for the other half of that file.

My printer device looks like this:
```
ls -l /dev/lp0
 crw-rw---- 1 root lp 6, 0 2008-06-01 17:14 /dev/lp0

```
And I'm not part of the lp group, but this should add you to it:
```
sudo usermod -a -G lp **yourname**
```

Regards
Iain

---

### Post by Paulo M. on 2008-06-03
Hi tinivole!
Thanks one more time, and I'm sorry, but yesterday I couldn't access forum... maintenance stuff, it said..:!
I can't make "touch ~/.stylus-toolbox.conf" code ... terminal says I have no permissions for that.
And I can't still run the application, of course!

All my best !

---

