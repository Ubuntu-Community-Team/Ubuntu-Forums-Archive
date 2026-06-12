---
title: "Permissions"
date: 2013-11-14
forum: General Help
---

### Post by raminzeb on 2013-11-14
Hi

Over the last few years ive jumped around between distros for both curiosity and experimentation. Every time ive done this i have kept my home folder under the same username and password. Obviously difference distros have changed the permissions in my home folder. I noticed some, like ubuntu list me under my own group username (1000), where as others under the users (100) group.

anyway I'm now back on ubuntu and to stay. Im using 12.04.

After my first install i set my permissions as they should be in ubuntu, i followed this very helpful guide:
[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

Now, if I 
```
ls -l 
```
my home directory, this is my output:

```
drwxr-xr-x    2 username username  4096 Nov 14 17:48 Desktop
drwxr-xr-x    3 username username 4096 Nov 14 12:44 Documents
drwxr-xr-x   11 username username 4096 Nov 14 17:42 Downloads
drwx------    9 username username 4096 Nov 14 15:25 Dropbox
drwxr-xr-x  358 username username 12288 Nov 14 12:20 Music
drwxr-xr-x.  14 username username 4096 Nov 12 23:05 Pictures
drwxr-xr-x    2 username username 4096 Nov 14 12:03 Public
drwxr-xr-x    2 username username 4096 Nov 14 12:03 Templates
drwxr-xr-x    3 username username 4096 Nov 14 12:20 Videos
```

I have replaced my username with the text username but you can see thats what is set for both my user and group.

now ignoring dropbox (if i should i ignore its permission - it was created by the program itself when i installed dropbox AFTER installation), my main worry is the dot (.) at the end of my Pictures permissions.

I read that this is something to do with security in linux? but im confused how it ended up there? I'm also concerned because if i cd into other directories, such as Music and ls -l random files seem to have this dot at the end of the permissions. eg:

```
drwxr-xr-x.  3 username username 4096 May 22  2012 Anstam
drwxr-xr-x.  6 username username 4096 Jan 28  2012 Arcade Fire
drwxr-xr-x.  4 username username 4096 Jan 28  2012 Architecture in Helsinki
drwxr-xr-x.  5 username username 4096 Jan 28  2012 Archive
drwxr-xr-x.  3 username username 4096 Jan 28  2012 Arctic Monkeys
drwxr-xr-x.  3 username username 4096 Jan 28  2012 Arrested Development
drwxr-xr-x   3 username username 4096 Mar 17  2013 Atoms For Peace
drwxr-xr-x.  5 username username 4096 Jan 29  2012 A Tribe Called Quest
```

this behaviour is the same for Documents, Pictures etc.

In this thread
[http://ubuntuforums.org/showthread.php?t=1315684](http://ubuntuforums.org/showthread.php?t=1315684)

he states that to strip the dot from the files you can use the following command:

```
find . -print0 |xargs -0 -n 1 sudo setfattr -h -x security.selinux
```

However, it doesnt work here as I get the error:
```

sudo: setfattr: command not found
```

Anyway, what I'm more interested in is what that dot specifically means and how it might have appeared in my files. Can they corrupt the files, do nasty things? is it dangerous for them to be in that state and what can i do to get rid of it.

I made a new ubuntu account and did some tests on the files and none of them have that dot placed at the end of the permissions.

any help would be appreciated. cheers.

---

### Post by bab1 on 2013-11-14
> **raminzeb said:**
> Hi

Over the last few years ive jumped around between distros for both curiosity and experimentation. Every time ive done this i have kept my home folder under the same username and password. Obviously difference distros have changed the permissions in my home folder. I noticed some, like ubuntu list me under my own group username (1000), where as others under the users (100) group.

anyway I'm now back on ubuntu and to stay. Im using 12.04.

After my first install i set my permissions as they should be in ubuntu, i followed this very helpful guide:
[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

Now, if I 
```
ls -l 
```
my home directory, this is my output:

```
drwxr-xr-x    2 username username  4096 Nov 14 17:48 Desktop
drwxr-xr-x    3 username username 4096 Nov 14 12:44 Documents
drwxr-xr-x   11 username username 4096 Nov 14 17:42 Downloads
drwx------    9 username username 4096 Nov 14 15:25 Dropbox
drwxr-xr-x  358 username username 12288 Nov 14 12:20 Music
drwxr-xr-x.  14 username username 4096 Nov 12 23:05 Pictures
drwxr-xr-x    2 username username 4096 Nov 14 12:03 Public
drwxr-xr-x    2 username username 4096 Nov 14 12:03 Templates
drwxr-xr-x    3 username username 4096 Nov 14 12:20 Videos
```

I have replaced my username with the text username but you can see thats what is set for both my user and group.

now ignoring dropbox (if i should i ignore its permission - it was created by the program itself when i installed dropbox AFTER installation), my main worry is the dot (.) at the end of my Pictures permissions.

I read that this is something to do with security in linux? but im confused how it ended up there? I'm also concerned because if i cd into other directories, such as Music and ls -l random files seem to have this dot at the end of the permissions. eg:

```
drwxr-xr-x.  3 username username 4096 May 22  2012 Anstam
drwxr-xr-x.  6 username username 4096 Jan 28  2012 Arcade Fire
drwxr-xr-x.  4 username username 4096 Jan 28  2012 Architecture in Helsinki
drwxr-xr-x.  5 username username 4096 Jan 28  2012 Archive
drwxr-xr-x.  3 username username 4096 Jan 28  2012 Arctic Monkeys
drwxr-xr-x.  3 username username 4096 Jan 28  2012 Arrested Development
drwxr-xr-x   3 username username 4096 Mar 17  2013 Atoms For Peace
drwxr-xr-x.  5 username username 4096 Jan 29  2012 A Tribe Called Quest
```

this behaviour is the same for Documents, Pictures etc.

In this thread
[http://ubuntuforums.org/showthread.php?t=1315684](http://ubuntuforums.org/showthread.php?t=1315684)

he states that to strip the dot from the files you can use the following command:

```
find . -print0 |xargs -0 -n 1 sudo setfattr -h -x security.selinux
```

However, it doesnt work here as I get the error:
```

sudo: setfattr: command not found
```

Anyway, what I'm more interested in is what that dot specifically means and how it might have appeared in my files. Can they corrupt the files, do nasty things? is it dangerous for them to be in that state and what can i do to get rid of it.

I made a new ubuntu account and did some tests on the files and none of them have that dot placed at the end of the permissions.

any help would be appreciated. cheers.

Before anything else is done you should back up all of you files at  /home  This is really just a safety precaution.  You should be doing this anyway on a regular basis.  

It's not a good idea to run any command  unless you really understand what it ramifications it has on your file system (in this case). 

The dot symbol (.) indicates that extended security attributes have been added to most everything in the /home directory.  It ended up there because you moved the partition to a version of Linux that uses SELinux for security.  Most likely a version of Redhat/CentOS.  is it dangerous to leave it like that?  Probably not.  But is is simple to clean it up for Debian/Ubuntu use.

The command is actually 2 commands (one piped into another.  The first part uses find to locate all the directories and files from the users* current directory*  (they are stored in RAM for future use```
find . -print0 
```... then it  pipes the information  ( | )  to the second command the uses the  root user to execute the command setfattr which deletes the security attribute without following any sym-links it encounters ```
xargs -0 -n 1 sudo setfattr -h -x security.selinux
```

If you type *cd* with no argument the system makes your current directory your home directory ( ~ ).  If you or any other users have files in /home,  you need to start by using this command ```
cd /home
```...before you use the incantation```
find . -print0 |xargs -0 -n 1 sudo setfattr -h -x security.selinux
```

As you say the command doesn't work in Ubuntu by default.  A simple Google search on the keyword:  **settattr** would have revealed  the appropriate Ubuntu [man page]("http://manpages.ubuntu.com/manpages/gutsy/man1/setfattr.1.html").  A little reading would get  you to the the [package attr]("http://packages.ubuntu.com/search?keywords=attr") and additional info [here]("http://www.techrepublic.com/blog/linux-and-open-source/learn-to-use-extended-file-attributes-in-linux-to-boost-security/").  All of this is to say.  It's a good thing to be self sufficient (RTM).

Just add that package [attr]("http://packages.ubuntu.com/search?keywords=attr"), place yourself in the correct current directory and reissue the command again and all should be good.  As always YMMV.

---

### Post by raminzeb on 2013-11-15
> **bab1 said:**
> Before anything else is done you should back up all of you files at  /home  This is really just a safety precaution.  You should be doing this anyway on a regular basis.  

It's not a good idea to run any command  unless you really understand what it ramifications it has on your file system (in this case). 

The dot symbol (.) indicates that extended security attributes have been added to most everything in the /home directory.  It ended up there because you moved the partition to a version of Linux that uses SELinux for security.  Most likely a version of Redhat/CentOS.  is it dangerous to leave it like that?  Probably not.  But is is simple to clean it up for Debian/Ubuntu use.

The command is actually 2 commands (one piped into another.  The first part uses find to locate all the directories and files from the users* current directory*  (they are stored in RAM for future use```
find . -print0 
```... then it  pipes the information  ( | )  to the second command the uses the  root user to execute the command setfattr which deletes the security attribute without following any sym-links it encounters ```
xargs -0 -n 1 sudo setfattr -h -x security.selinux
```

If you type *cd* with no argument the system makes your current directory your home directory ( ~ ).  If you or any other users have files in /home,  you need to start by using this command ```
cd /home
```...before you use the incantation```
find . -print0 |xargs -0 -n 1 sudo setfattr -h -x security.selinux
```

As you say the command doesn't work in Ubuntu by default.  A simple Google search on the keyword:  **settattr** would have revealed  the appropriate Ubuntu [man page]("http://manpages.ubuntu.com/manpages/gutsy/man1/setfattr.1.html").  A little reading would get  you to the the [package attr]("http://packages.ubuntu.com/search?keywords=attr") and additional info [here]("http://www.techrepublic.com/blog/linux-and-open-source/learn-to-use-extended-file-attributes-in-linux-to-boost-security/").  All of this is to say.  It's a good thing to be self sufficient (RTM).

Just add that package [attr]("http://packages.ubuntu.com/search?keywords=attr"), place yourself in the correct current directory and reissue the command again and all should be good.  As always YMMV.

Hi bab1, thanks for this.

I installed the package and did the deed on a few test files and folders and when i was sure everything was ok, did so on my home folder. i do keep backups.

I actually suspected the attr package wasnt installed on my system, but i wanted advice on whether the package was still used and was safe to use, as the original thread with the command was quite a few years old. i spent the last few days reading up about user / groups and permissions on the arch wiki, hence me noticing the problem my file system had.

anyway i guess we now have a definitive answer for this that can hopefully help others in the future. again, thank you. i guess we can mark this as solved.

---

