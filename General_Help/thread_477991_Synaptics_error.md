---
title: "Synaptics error"
date: 2007-06-18
forum: General Help
---

### Post by SombreDoom on 2007-06-18
I was trying to open up synaptics to add a repositories but I get this message. 

>  Failed to check for installed available applications.

This is a major failure of your software management system. Please check for broken packages  with synaptic, check for the file permissions and correctness of the file' /etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'. 



I get this error message when i first up the Synaptics manager. Any help would be appreciated, thanks in advance.

---

### Post by SombreDoom on 2007-06-18
Also when I try to do something in the terminal I get this error.

>  E: Type 'sudo' is not known on line 44 in source list /etc/apt/sources.list 

---

### Post by SombreDoom on 2007-06-18
Can anyone help me?

---

### Post by SombreDoom on 2007-06-18
bump

---

### Post by trginter on 2007-06-19
Just received this same error.  Anyone got any suggestions?

---

### Post by beatbros on 2007-06-19
Hi,
Please  post your /etc/apt/sources.list

---

### Post by WW on 2007-06-19
A similar problem was reported here: [http://ubuntuforums.org/showthread.php?t=462418](http://ubuntuforums.org/showthread.php?t=462418)

Something you did has created an incorrect entry in the file /etc/apt/sources.list.  Since several people have reported similar problems, I wonder if you all followed the same set of instructions from somewhere, or ran the same script for installing something.

Whatever the reason, if you post the file /etc/apt/sources.list here, we can try to figure out how to fix it.

---

### Post by WW on 2007-06-19
The other thread mentions installing wine.  After reading [this page]("http://www.winehq.org/site/download-deb"), I have a guess for what the problem is.  The instructions on the Wine web page are potentially misleading. They say "Next, add the repository to your system's list of APT sources:", and give a line like (for Feisty):
```

sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list -O /etc/apt/sources.list.d/winehq.list

```
Those instructions might be interpreted to mean "add the line to sources.list", but in fact that is a *command* to be run in a terminal.  To test this, I added the line to my sources.list, and tried to do an Update in Synaptic. I got exactly the error reported in SombreDoom's second post, and in the other thread.

If this is what has happened, you must removed the line that begins with sudo from /etc/apt/sources.list, and instead enter that line as a command in a terminal.

---

### Post by SombreDoom on 2007-06-19
thanks for the help guys but I don't know what you mean. Do you what me to post my directory?

/etc/apt/sources.list.d

---

### Post by WW on 2007-06-19
There is a file called /etc/apt/sources.list *and* a directory called /etc/apt/sources.list.d.  Post the file.

---

### Post by SombreDoom on 2007-06-20
I get an error message when I try to upload the file.

---

### Post by beatbros on 2007-06-20
hi,

sudo gedit /etc/apt/sources.list
Menu Edit / Select all
Copy
Paste in your reply.

---

### Post by SombreDoom on 2007-06-20
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://bi.archive.ubuntu.com/ubuntu/](http://bi.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
sudo apt-get install affinity-svn
    * ## Avant Window Navigator
    * deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
    * deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

---

### Post by Rui Pais on 2007-06-20
hi.
 
Broken apt.sources ;)
do:
```
gksudo /etc/apt/sources.list
```
and change the last 4 lines from:
> sudo apt-get install affinity-svn
* ## Avant Window Navigator
* deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
* deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

TO THIS:
> 
## Avant Window Navigator
deb [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42/](http://download.tuxfamily.org/syzygy42/) feisty avant-window-navigator

To avoid errors delete your 3 lines and copy+paste lines from my post.
then:
sudo apt-get update 
and thats all. :)

---

### Post by SombreDoom on 2007-06-20
I did as you told me and I get this error.

>  E: Type 'sudo' is not known on line 44 in source list /etc/apt/sources.list
john@john-laptop:~$ 




---

### Post by Rui Pais on 2007-06-20
Oops my mistake, not cutting enough.
I correct m previous post. Just delete the line 44, the one that says:
sudo apt-get install affinity-svn

---

### Post by SombreDoom on 2007-06-20
Thank you so much, mate!

---

