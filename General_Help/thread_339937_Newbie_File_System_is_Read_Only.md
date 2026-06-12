---
title: "Newbie File System is Read Only??"
date: 2007-01-16
forum: General Help
---

### Post by Shenook on 2007-01-16
I have a fresh install of UBUNTU.  I tried to install a video driver but it comes up with an error like it can't even write to a temp folder.  I checked my drive and folders and even though I am part of the root group I can't change permissions on any folder.  Under the File system if I go to properties it shows the owner as "unknown."  Any ideas?

---

### Post by Sqwishy on 2007-01-16
What exactly are you trying to do. You probably need to be root, in console type 'sudo' before anything you do if you need to be root.

---

### Post by taurus on 2007-01-16
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Shenook on 2007-01-16
That's the thing though.  When I go to my file system even my "create Folder" option is greyed out even though I'm part of the root group.

When I try to install with Sudo I get an error trying to install my video driver from ATI.

I Get the following:

./ati-installer.sh: 165: Syntax Error: Bad Substitution
Removing Temporary Directory: fglrx-install

---

### Post by taurus on 2007-01-16
Does it happen to be ntfs filesystem?

If you want to install an ATI driver for your graphic card, perhaps this guide would help.

[http://albertomilone.com/driver.html](http://albertomilone.com/driver.html)

---

### Post by Shenook on 2007-01-16
AFter trying to install the video driver the system ran into some crash.  But I tried to save the crash info but I don't have rights to save anything anywhere in the computer.  Why is there only read only on everything with an unknown owner?

How can I even create a directory if the whole drive is read-only?  I'm booting off my hard drive and I don't get it.

---

### Post by taurus on 2007-01-16
Where do you want to save it to and what filesystem is it?

Can you post the outputs of these commands from a terminal?

```
cat /etc/fstab
sudo mount
```

---

### Post by zerhacke on 2007-01-16
> **Shenook said:**
> That's the thing though.  When I go to my file system even my I'm part of the root group.
Removing Temporary Directory: fglrx-install

Root is disabled on Ubuntu systems.  This is why even though you're in the root group you cannot do things root would normally be allowed to do.

Instead, try using the terminal, and preface each command you would like to do as root with the word "sudo" minus the quotes.  For example,

```
sudo mkdir /mnt/directory
```

You'd substitute mkdir /mnt/directory with whatever command it is that you would like to do.

---

### Post by Shenook on 2007-01-16
So for example I make a temp directory using SUDO credentials.  When I log in as me I still won't have rights to create a simple open office document because it's read only?

---

### Post by taurus on 2007-01-16
Unless you change the owner of that directory to your username, then you can read and write to it.

---

### Post by Shenook on 2007-01-16
What is the basic command to change permissions on directories?  Could you point me to a link so I can study up?  Thx for all the help thus far.  Was able to create the directory but can't add anything yet.  Will figure this out soon enough.

---

### Post by taurus on 2007-01-16
```
sudo chown -R **username**:**username** <directory name>
```
(where **username** is the actual name that you log in...)

That would make username the owner of that directory but better be careful what directory you change the owner to.  Changing the wrong directory will cause some serious problems to your system.

---

