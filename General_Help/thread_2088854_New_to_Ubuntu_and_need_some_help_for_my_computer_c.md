---
title: "New to Ubuntu and need some help for my computer class"
date: 2012-11-27
forum: General Help
---

### Post by JaviJ01 on 2012-11-27
I am currently taking a class on Operating Systems and this week we are going over Linux. My teacher wants us to install a Linux OS and then do some basic things on it. Ive install Ubuntu onto a VM already but have no idea what I am doing. I posted the 4 questions/things I need to do and was hoping someone may be able to help me out/point me in the right direction as to doing them?

Any and all help would be appreciated!!!


Start the Linux as your main operating system

Task should be done in Command Language:

1. Create 3 user accounts (user1, user2 and user3), write down the steps  (use only command language)

2. Create a group ( Group A) and put all 3 users above in the same group as Group A , and write the detail steps

3. Create a share folder name it as Share1, and give access Share1 to Group A, write also the steps in detail

4. Change the permission of Share1 only for Group A as read write and execute , and none for others, except for the root as the owner , write in detail

Please write detail steps and post it

---

### Post by LuisGMarine on 2012-11-27
If you scroll down towards the "Adding and Deleting Users", it should answer all your questions as to how to go about it.

[https://help.ubuntu.com/12.10/serverguide/user-management.html]("https://help.ubuntu.com/12.10/serverguide/user-management.html")

---

### Post by TheFu on 2012-11-27
No. We will not do your homework for you.  The OS has built-in "help" that explains how to accomplish these things. I will help with htat.

# open a terminal
# type "man man" without the quotes.
# search for appropriate commands using "apropos {subject}" - "apropos user" should get you started on the first task.  "apropos permission" should get you on the right track for the last task.

Good luck.  The journey for knowledge is part of the assignment.

---

### Post by JaviJ01 on 2012-11-27
I wasn't asking you to do my work for me, sorry if that's how it came across. I've been able to figure out how to create users/groups through google searching so thank you for the help LuiGMarine. Now I just need to figure out how to create a share folder. Thank you both though

---

### Post by LuciferRex on 2012-11-27
I love that you are required to use Linux for a class!

---

### Post by JaviJ01 on 2012-11-27
Im having trouble researching the share folders part, I keep seeing something about Samba? Do i have to install that to create the shared folder part?

---

### Post by Lars Noodén on 2012-11-27
> **JaviJ01 said:**
> Im having trouble researching the share folders part, I keep seeing something about Samba? Do i have to install that to create the shared folder part?

You can do it with the system's default permissions.  Here is a little background reading:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by TheFu on 2012-11-27
Samba is the server-side of sharing a folder from Linux to Windows.

Or you can use NFS, which is easier.  There are extensive "how-to" guides for both methods.

Sorry that I assumed you wanted us to do the work for you.  If you look for howtoforge and samba, I'm sure you can find a guide. There are some great documents on ubuntu.com for this stuff too.

---

### Post by LuisGMarine on 2012-11-27
lol I also assummed you wanted us to do the homework for you, although I have to say I was tempted lol.  

As for the "share" part of your homework; did your teacher say that the share folder has to be accessed over a network or just locally?  If it is over a network, then yeah you are going to have to involve samba. However I feel like the question just wants you to create a folder, give permission to a select group, and add certain users to that group.  There is no need to make things more complicated by overthinking the question.

---

### Post by JaviJ01 on 2012-11-27
Ok I think I have done most of the work but now im stuck on #4 of my questions and hopefully can get a little bit of direction as where to look. Currently I have done this so far and would love if someone can look over it to make sure it looks ok.

 1.To create a new user I used: 
  Adduser User1
Adduser User2
Adduser User3
  2.To create a new group:
Sudo addgroup group a
  To add an existing user to an existing group you can use the same command:
Sudo adduser user1 group a (repeated for user2/3)
  3.To make the share folder:
Mkid share1
  To give access of Share1 to Group A:
Sudo chgrp groupa share1
  
I am looking throught the link Lars Nooden posted but I am not sure where exactly I should be looking, it honestly all looks so confusing lol.  

I tried: "chmod ug+rwx share1" and "chmod 770 share1" but I dont think that did anything. 
[]("http://ubuntuforums.org/member.php?u=168643")

---

### Post by LuisGMarine on 2012-11-28
I'm not sure if the commands that you posted on here were accurate as far as the case sensativity ...

In step 2 and 3, the group you created is "group a" and in step 3, the group you added to the share1 folder was "groupa".  Not sure if you forgot the space between the two letters, but this could be your problem.

As for the last step, it should be something like this:

```
sudo chmod ug+rwx share1
```

Also if you navigate to where the "share1" folder is, what is the output of this command when you type it into terminal?

```
ls -l
```

---

### Post by TheFu on 2012-11-28
chmod only changes the permissions, not the owner or group. You'll want to look into **chgrp **and **chown** commands for those.

Also, I think someone else said it already, but your commands above do not appear to be correct.  All commands on UNIX systems are case sensitive.  "Sudo" and "sudo" are different commands - on 99.99999% of the systems, "sudo" is the command you meant.  I've never used **mkid** in my life. Is that really the command you want?

I also think that Lars is correct. We are over thinking your "share folder" exercise.  Local shared folders are easy.  Here's an outline:
* create the folder someplace that every end-user who needs access can get to.
* create a group that all end-users are members of.
* force the directory group ownership to be that new group.
* to force all files and directories below that new directory to retain the specific new-group you've already set, look into **chmod g+s** command.  Otherwise, the default group for each user will get used and on Ubuntu systems, these will be username:username - almost never what you really want.
* change the permissions on the new folder so that the group has write permissions. In a group working environment, setting the **umask** to be 007 or 005 is often a good idea too.  If you decide to do this, adding the umask setting to the startup profile for each end-user is probably best.  That is in /etc/default/{shell}, I believe.

There are many ways to accomplish the same end goals.  I'm not positive that I didn't leave something important out in those outlined steps.  Test everything.  It is also a good idea to create a written step file ... like a script, so you can test and retest everything over and over until you get it 100% correct.

---

