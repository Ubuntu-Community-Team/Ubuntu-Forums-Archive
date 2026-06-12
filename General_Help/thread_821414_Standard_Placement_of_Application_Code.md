---
title: "Standard Placement of Application Code"
date: 2008-06-07
forum: General Help
---

### Post by mrund on 2008-06-07
I've downloaded a useful program that works well under my Ubuntu installation. It is in a file folder currently sitting on my desktop. I don't want it there. So here's a really basic unix question.

Where is the typical residence of application code in a unix system, the equivalent of Windows' "Program Files" directory? Where should I move the folder before creating a link icon for it on my desktop?

---

### Post by LoneWolfJack on 2008-06-07
in linux, all your stuff resides in 
/home/<yourusername>/

if you don't want it on your desktop, move it there (your desktop is in /home/<yourusername>/Desktop btw.)

unless you really know what you are doing, you want nothing installed outside of this directory. all official packages will automatically go to the right place when installed.

---

### Post by nick_h on 2008-06-07
What program is it?  What files does it contain?

If it is a single executable you could place it in your ~/bin folder. If you want all users on the system to be able to run it then put it in the /usr/local/bin folder.

If it is a bigger application then it is usual to install it under the /opt directory structure.

---

### Post by mrund on 2008-06-07
It's jUploadr, an app for uploading pix to Flickr. It comes as a folder with a few files and subfolders. I can't find it on Synaptic.

[http://juploadr.org/](http://juploadr.org/)

---

### Post by nick_h on 2008-06-07
I would probably create a directory under /opt for it.

---

### Post by mrund on 2008-06-07
Opt as in "optional"? But then the other users wouldn't have access to it?

---

### Post by nick_h on 2008-06-07
Yes, /opt is a standard place to install non packaged programs.

[http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/)

You could give permissions for any user to use the program.

---

### Post by mrund on 2008-06-07
Thanks. And (briefly), how then do I manage other users' rights to individual programs?

Is there, for instance, a simple way to remove password protection from Wifi Radar?

---

### Post by mike2357 on 2008-06-07
Regardless of whether you choose /opt or /usr/local/bin, other users would have access to it depending on UNIX permissions.

nick_h is exactly right, because it's not a good idea to put anything you get outside of Ubuntu distributions in directories that Ubuntu installs programs in, such as /bin or /usr/bin.  

Generally when I get something outside of Ubuntu, I make a directory in /usr/local and put what I download in it.  If the installation script doesn't copy executable files to /usr/local/bin, I can do so manually.  By using that strategy, /usr/local/bin only has executable programs, rather than numerous source code files from any number of programs.

---

### Post by nick_h on 2008-06-07
> I make a directory in /usr/local and put what I download in it. If the installation script doesn't copy executable files to /usr/local/bin, I can do so manually.
Yes, /usr/local is just as good.  Create a separate directory to keep it separate from other applications.  You could create a symlink in the /usr/local/bin directory, which should be in your PATH.

> a simple way to remove password protection from Wifi Radar?
I think it is a system application, I expect that it needs a password for security reasons.

Use Unix permission to control access.  If you want any user to run a program give execute permission to all.
```
chmod a+x filename
```
If you want just members of a group to run a program just change the group ownership and give execute permision to group.
```
chgrp mygroup filename
chmod g+x filename
```

---

### Post by mrund on 2008-06-07
Strangely enough, I'm not allowed to copy anything into usr/local or usr/local/bin. And I'm root. WTF?

---

### Post by nick_h on 2008-06-07
> Strangely enough, I'm not allowed to copy anything into usr/local or usr/local/bin. And I'm root.
If you have root permissions then you will be able to copy into those directories.  How are you trying to copy the files?

---

### Post by mrund on 2008-06-07
Drag 'n' drop from my desktop. Having had intermittent trouble with moving entire directories in this manner, I've also tried creating a new directory for the files by right-clicking in the file manager window for usr/local/bin. The "Create Folder" item was greyed out on the context menu.

---

### Post by nick_h on 2008-06-07
If you want to use drag 'n' drop then try starting nautilus as root:
```
gksudo nautilus
```
Be careful when using it as root and close it when you are finished.

---

### Post by cariboo on 2008-06-07
The easiest way to move files is to open a terminal cd in to the directroy the files are in an type the following:

```
sudo mv filename /usr/local/bin
```

Then once they are there:

```
cd /usr/local/bin [enter]
sudo chmod root.root * [enter]
sudo chmod 755 * [enter]

```

This changes the ownership to root and allows everybody to execute the program but not change it.The enter in square brackets means of course hit return.

Good luck

Jim

---

### Post by mrund on 2008-06-09
Oh man, this is driving me nuts. The "gksudo nautilus" solution works some of the time when I need to move stuff between accounts, but it's completely flaky and often has to be restarted. One of the things it definitely does not like is when I try to drag and drop nested catalogues -- and this is of course one of the most labour-saving and thus desirable things I'm trying to do.

As for the command-line solution, I used to know my way around an MS-DOS system, but here I don't know what my own catalogue structure is like and the prompt doesn't tell me where in that structure I currently am.

As I described in another thread, one of my user accounts has gone autistic, and I need to copy that user's mailbox out in order to graft it onto a newly created account. But I can't get all that stuff out of the zombie account.

---

