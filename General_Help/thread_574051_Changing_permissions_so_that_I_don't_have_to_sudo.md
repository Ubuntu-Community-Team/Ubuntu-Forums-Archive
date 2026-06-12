---
title: "Changing permissions so that I don't have to sudo"
date: 2007-10-12
forum: General Help
---

### Post by cappii on 2007-10-12
Howdy from Texas.  I am trying to install a program that is to be used by High School students.  The program only opens in terminal by sudo sh start.sh.  However, I cannot give the students SUDO permissions over the computer, as they would likely mess things up.  So, I created a launcher on the desktop to make that part easier, but, it still requires sudo to be included in the command line.  I installed the program giving them Administrative access, however, I am forced to take that access away from them.
Progress so far:  I have chmod'd a=rx for all users.  Chown'd to student:root.  And put the student username in the root group.   Also changed the launcher to exclude "sudo" in the command line.  Still, however, when launching from the shortcut, the terminal pops up, goes through startup, and shuts down. 
 I am trying to make a change here from using Win 2k computers to using Ubuntu, to try to give the kids a slightly broader horizon, however, unless I can make this work without having to "sudo" I will not be able to put these machines out for their use.  Any help would be greatly appreciated. :confused:

---

### Post by Namtabmai on 2007-10-12
What about putting all the users you want to use this program into a certain group, or just user the users group if you want everyone to be able to do this.

Then edit your /etc/sudoers file and add something like
```

%users 127.0.0.1 = NOPASSWD: /path/to/executable

```

That will allow all users in the group users to execute the file /path/to/executable on the host 127.0.0.1 without having to enter a password. Note that they won't be able to sudo any other executable.

---

### Post by cappii on 2007-10-12
Thanks for that tip :) .  I used visudo and changed / added what you typed, precluded by a description.  However, the issue still remains.  I tried editing the launcher to disclude the "sudo" in the command line also, however, it was to no avail.  When "sudo" was included, the terminal immediately shut down after entering the password... as student is not in the sudoers file.  When excluding "sudo", and this is likely more due to the previous changes that were made, the startup begins, then shuts down.  Again, because of the sudoers.  Any more suggestions?

---

### Post by Namtabmai on 2007-10-12
O.k. you need to include the sudo before the command so that it gets executed with root access. But you need to make sure that the student is in a group that is allowed to execute that command. In the example I gave, the group was users, so check that the users are in that group. 
e.g.
log in as the student and
```

groups

```
And make sure that they belong to that group.

Also try running the command from the command line to make sure it works before putting it into a launcher.

If that fails try changing the line too
```

%users ALL = NOPASSWD: /path/to/executable

```

And trying again.

---

### Post by az on 2007-10-12
> **cappii said:**
> Howdy from Texas.  I am trying to install a program that is to be used by High School students.  The program only opens in terminal by sudo sh start.sh.  However, I cannot give the students SUDO permissions over the computer, as they would likely mess things up.  So, I created a launcher on the desktop to make that part easier, but, it still requires sudo to be included in the command line.  I installed the program giving them Administrative access, however, I am forced to take that access away from them.
Progress so far:  I have chmod'd a=rx for all users.  Chown'd to student:root.  And put the student username in the root group.   Also changed the launcher to exclude "sudo" in the command line.  Still, however, when launching from the shortcut, the terminal pops up, goes through startup, and shuts down. 
 I am trying to make a change here from using Win 2k computers to using Ubuntu, to try to give the kids a slightly broader horizon, however, unless I can make this work without having to "sudo" I will not be able to put these machines out for their use.  Any help would be greatly appreciated. :confused:

The problem is that your applications needs root privileges to run.  That is not acceptable.  

Why do you need to run this as root?

---

### Post by cappii on 2007-10-27
That is the question, actually.  I DON'T want to run it as root.  However, I cannot install it without sudoing the install.sh file.  It has to install it's own java... doesn't like the newer Javas.  Anyways, as I have noted, I have it to where it pops up a terminal box and prompts for a sudo password, and that only works if the students are in the sudoers group... which is a very bad idea.  Most of these kids only know Mac and Windows, and wouldn't know that they have the ability to administer the system, or how... but there is always one... and that one can potentially cause damage.

---

### Post by #Reistlehr- on 2007-10-27
Right, you cant install it, because when it installs, it will probably place files throughout the entire filesystem, (ie, /usr, /etc), and a regular user cannot write there.

So, you need to use sudo when you install it. But you should be able to chmod the executable after it is installed (ie sudo chmod 777 /etc/program/executable)

If that is the case, anyone can run the file.

---

