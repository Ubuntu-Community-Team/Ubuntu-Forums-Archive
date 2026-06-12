---
title: "Root Directory question"
date: 2015-01-24
forum: General Help
---

### Post by michael-piziak on 2015-01-24
Is this the Root Directory.  See screenshot below

I notice that if I continue to type cd ..  it eventually will go no deeper than this.

Also, a question about this directory:  Why can't I right click a folder and make a link to any folder or file in this directory ?

---

### Post by sammiev on 2015-01-24
If I'm correct everything up to your home directory is owned by the root. Where your user name begins belongs to the user.

---

### Post by buzzingrobot on 2015-01-24
The name of the root directory is '/'.  A directory called '/root' also exists, but it is not the root directory. (Really).

The root directory is the 'root' of the file system.  All other directories are organized hierachically to be subordinate, or "within" the root directory.

In a terminal, something like "/usr/bin/AmazingApp" represents the path to the file called 'AmazingAPP'. It begins at the root directory (/), then the 'usr' directory, then the 'bin' directory, and then the file itself.

In GUI file managers, the root directory is commonly labeled "File System" or "Computer" or some such label.

Linux systems have a /home directory. Each user -- there can be more than one -- has his or her own directory created in the /home directory.  For example, a user named "Bob" has his own home folder named "Bob" in the system's /home directory: /home/Bob. If an account for user Sally is created on the same machine, she gets her own folder: /home/Sally. 

The "cd" command is used to change directories.  The '..' expression represents the directory one level up in the hierarchy. So, "cd .." takes you one level up, until you get to '/'.

---

### Post by deadflowr on 2015-01-24
> Also, a question about this directory: Why can't I right click a folder and make a link to any folder or file in this directory ?

Because you don't have write permission outside of your own home folder you can't make a link, normally.
(And the Home Folder(nautilus) only lets you make a link inside whichever directory you are in...)
 
But if you follow along with [your other thread]("http://ubuntuforums.org/showthread.php?t=2262390"), you can make a simple link .desktop file
You cabn do this in any text editor; gedit, or even vim or nano, if you want.
A simple one would be
[Desktop Entry]
Name=what you want to call the link
Type=Link
URL=file:///path/to/folder/file
Icon=whatever you want

save it as *something.desktop* where ever you please.
Now when you go into the folder where you saved this file, you should see a folder with it's Name,;from the Name= entry, and a link arrow.

---

### Post by ajgreeny on 2015-01-24
The entry called File System is commonly called root, but there is a folder within that also called /root, which is actually the home directory for the user root; although that user account is disabled in Ubuntu the folder still exists.

The /home directory that is highlighted in your pic is the folder in which all user folders are situated, so if you have more than one user on your computer there will be a folder within /home for each of them.

I think, though I am not certain, that in Linux distros where the root user is not disabled as it is in Ubuntu, there will also be a root named folder within the /home folder in the file system.  I have used other distros which use a root user and root password, but not for so many years that I simply can not remember if that is correct.

---

### Post by deadflowr on 2015-01-24
> I think, though I am not certain, that in Linux distros where the root  user is not disabled as it is in Ubuntu, there will also be a root named  folder within the /home folder in the file system.  I have used other  distros which use a root user and root password, but not for so many  years that I simply can not remember if that is correct. 				

Ubuntu, as shown, has it's own /root folder which is root's personal home folder. Outside of the normal /home directory. 
I too, can't remember the typical layout of a system which uses root users(or users who run as root), but I don't think Ubuntu uses a file system that is not in some way a standard design.

---

### Post by kjohri on 2015-01-24
> Is this the Root Directory. See screenshot below

I notice that if I continue to type cd .. it eventually will go no deeper than this.

Yes, this is the root directory. The directory structure is in the form of an inverted tree. You can not go deeper than this because this is the top. 

> Also, a question about this directory: Why can't I right click a folder and make a link to any folder or file in this directory ? 

Hard links are not allowed but you can make symbolic links.
```

user1@host1:~$ ln /lib mylib
ln: ‘/lib’: hard link not allowed for directory
user1@host1:~$ ln -s /lib mylib
user1@host1:~$ ls -ls mylib
0 lrwxrwxrwx 1 user1 user1 4 Jan 25 07:01 mylib -> /lib

```

---

### Post by deadflowr on 2015-01-24
I don't think it's a matter of hard link or soft link. It's a matter of how nautilus allows making a link...
(Which, by the way, makes soft links)

---

### Post by Impavidus on 2015-01-25
The root user's home directory, /root, is not in /home but must always be on the root partition. This is so to have it available in single user mode (recovery mode &#8594; drop to root shell), when the /home partition, if it exists, is not mounted.

=======

The directory .. is always the current directory's parent directory. As you have noticed, the root directory has a parent directory, which has been defined as itself. Somehow people decided this made more sense than defining the root directory to have no parent, in which case **cd ..** eventually would lead to "No such file or directory".

---

### Post by ajgreeny on 2015-01-25
> **Impavidus said:**
> The root user's home directory, /root, is not in /home but must always be on the root partition. This is so to have it available in single user mode (recovery mode &#8594; drop to root shell), when the /home partition, if it exists, is not mounted.

=======

The directory .. is always the current directory's parent directory. As you have noticed, the root directory has a parent directory, which has been defined as itself. Somehow people decided this made more sense than defining the root directory to have no parent, in which case **cd ..** eventually would lead to "No such file or directory".
Thanks for that info Impavidus; it clears up my uncertainty about the site of /root in a standard Linux distro's filesystem.

---

