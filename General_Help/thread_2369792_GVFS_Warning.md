---
title: "GVFS Warning"
date: 2017-08-26
forum: General Help
---

### Post by raleigh3 on 2017-08-26
This occurs with both thunar and caja.

```
andy@7:~$ thunar

(thunar:15268): GVFS-WARNING **: can't init metadata tree /home/andy/.local/share/gvfs-metadata/home: open: Permission denied
```

Anything to be concerned about ?

I am the owner of said directory except for home which is root.

---

### Post by TheFu on 2017-08-28
Probably not.  

gvfs is part of gnome.  They (the gnome devs) like to think we use all their infrastructure stuff, including the gnome-virtual-file-system. There are some uses for it, under some specific needs. 

Perhaps **export GVFS_DISABLE_FUSE=1** in your ~/.profile will solve it? Logout and login to get the setting to be seen. When I tested, that caused even more errors to be displayed, most marked as "critical".  Always fun to see that. ;)

You could always redirect stdout + stderr to a log file or /dev/null, if you don't want to see these things.  [https://github.com/jlevy/the-art-of-command-line](https://github.com/jlevy/the-art-of-command-line) has some helpful methods to do this, among other things.

[https://wiki.gnome.org/Projects/gvfs/doc](https://wiki.gnome.org/Projects/gvfs/doc) has the gvfs documentation

---

### Post by mc4man on 2017-08-28
> **raleigh3 said:**
> 

I am the owner of said directory except for home which is root.
If referring to the file named home in that directory then root shouldn't own it. You can just go ahead & delete it. (As root if need be
It will come back with you as owner.

---

### Post by TheFu on 2017-08-28
Ah ... the OP probably ran some GUI tool (any file manager would do it) with sudo and broke the file permissions.  It is a bad idea to run most GUI tools with sudo.

---

### Post by mc4man on 2017-08-29
> **TheFu said:**
> Ah ... the OP probably ran some GUI tool (any file manager would do it) with sudo and broke the file permissions.  It is a bad idea to run most GUI tools with sudo.
Most likely..
you could run this & see if root or group of root owns any files, generally it shouldn't
(- I think bleachbit users would find a folder of root owned, aptitude could create a harmless root owned config..
```
ls -lAR |grep root
```

---

### Post by TheFu on 2017-08-29
I can't think of any harm that would happen by just fixing all the issues by running **sudo chown -R $USER:$USER  ~/** on any Ubuntu system. Can you?

There are all sorts of things that could/would create root-owned files/directories if run with **sudo**.  cpan is another, if a system-wide installation is desired for those perl modules/libraries.  There are probably thousands of programs which do this, but in all my time using Linux, only the GUI programs seem to cause issues - and only if they are run with sudo before all the other major GUI programs have been run WITHOUT sudo first.

The issue is **sudo** alone doesn't change the HOME environment variable.  To do that, use **sudo -H** - then I think this issue will go away, forever, but there would be other issues since root's environment is usually different from the environment of any end-user login.  Some things would stop working, but not any of the administration things. Gotta pick our poisons.

Not really the end of the world, but new users generally haven't had time or interest in learning about Unix file/directory permissions and haven't learned to *think in a multi-user way* like every OS out there does, except MS-Windows.

---

### Post by raleigh3 on 2017-08-29
Thanks for all the feedback.

Thunar and Caja are running fine with no issues.

---

### Post by mc4man on 2017-08-29
> **TheFu said:**
> I can't think of any harm that would happen by just fixing all the issues by running **sudo chown -R $USER:$USER  ~/** on any Ubuntu system. Can you?


Not really the end of the world, but new users generally haven't had time or interest in learning about Unix file/directory permissions and haven't learned to *think in a multi-user way* like every OS out there does, except MS-Windows.
It seems not a bad idea at all.
The problem is blogs & websites continue to post incorrect commands (or copy incorrect commands from other sites.
Classic example is 'sudo gedit' which at one time was fine. Any web search of that will find thousands of examples.
As of maybe 4 or so years ago sudo gedit started having some unintended, & no longer could be considered 'safe' 
Yet it's still slobbered all over, even when bloggers are warned.. (maybe the 'art' of blogging is more like the art of copying.

On recent example of someone who has been previous notified about this - 
[http://www.omgubuntu.co.uk/2017/02/how-to-enable-nautilus-csd-header-bar-ubuntu](http://www.omgubuntu.co.uk/2017/02/how-to-enable-nautilus-csd-header-bar-ubuntu)

---

### Post by raleigh3 on 2017-08-29
I found this file that keeps growly slowly.

.xsession-errors

Thankfully that file is recreated on each boot.

Most of the errors where "
GVFS-WARNING **: can't init metadata tree /home/andy/.local/share/gvfs-metadata/home: open: Permission denied"

---

### Post by TheFu on 2017-08-30
Please post:
```
ls -l /home/andy/.local/share/gvfs-metadata/home
```
Please use "code" tags, like I have, so things line up and are easy to see.  Might need to go up 1 or 2 levels.
I'm not a fan of gvfs.

---

### Post by raleigh3 on 2017-08-30
```
andy@7:~$ ls -l /home/andy/.local/share/gvfs-metadata/home
-rw------- 1 root 2272 08-14-2017 /home/andy/.local/share/gvfs-metadata/home
```

---

### Post by raleigh3 on 2017-08-30
andy@7:~$ ls -l /home/andy/.local/share/gvfs-metadata/home
-rw------- 1 root 2272 08-14-2017 /home/andy/.local/share/gvfs-metadata/home

Sorry for double post. I saw no way to delete it.

---

### Post by TheFu on 2017-08-30
There's the issue.  Somehow, someone, cause the file to be created with root.  Usually (99+% of the time) it was because someone ran a file manager with sudo.  Best not to do that.

BTW, the solution/fix has already been provided.  If you've already run the fix and this is still happening, you need to find the root cause.

If you are absolutely positive that nobody is using a file manager with sudo, then some other program being run with sudo is opening a file chooser, which is doing making the file anew with root as the owner.  That is not good.

---

### Post by mc4man on 2017-08-30
> **raleigh3 said:**
> ```
andy@7:~$ ls -l /home/andy/.local/share/gvfs-metadata/home
-rw------- 1 root 2272 08-14-2017 /home/andy/.local/share/gvfs-metadata/home
```
Also - did you actually delete that file? The date is curious...

---

### Post by raleigh3 on 2017-08-30
> **TheFu said:**
> There's the issue.  Somehow, someone, cause the file to be created with root.  Usually (99+% of the time) it was because someone ran a file manager with sudo.  Best not to do that.

BTW, the solution/fix has already been provided.  If you've already run the fix and this is still happening, you need to find the root cause.

If you are absolutely positive that nobody is using a file manager with sudo, then some other program being run with sudo is opening a file chooser, which is doing making the file anew with root as the owner.  That is not good.

I sometimes run thunar as root because that's the only gui way to change permissions etc.

For instance, I can't add a  copy a background to usr/share/backgrounds because it's owned by root.

Some I open two instances of thunar as a superuser and do the copy.

---

### Post by TheFu on 2017-08-30
> **raleigh3 said:**
> I sometimes run thunar as root because that's the only gui way to change permissions etc.

Don't do that. It is causing this problem.

There are solutions for it, but for now, just don't.

If you need to edit a system file, use **sudoedit**
If you need to copy/move a file into a system directory, do it from the CLI, for now.  Until you have a better understanding of permissions.

---

### Post by raleigh3 on 2017-08-30
O.K. Won't use thunar or caja as a superuser.

I changed /home/andy/.local/share/gvfs-metadata/home to root.

No longer seeing any error messages. :-)

So how do I copy and move files from non root dirs to root ones via CL ?

---

### Post by #&amp;thj^% on 2017-08-30
have a look: [https://askubuntu.com/questions/594769/how-to-copy-files-in-terminal-as-root-user](https://askubuntu.com/questions/594769/how-to-copy-files-in-terminal-as-root-user)

---

### Post by raleigh3 on 2017-08-30
Thanks.

I am trying to make a script with replaceable parameters or else make an alias.

Less typing is always a good thing. :-)

I may be back.

---

### Post by raleigh3 on 2017-08-30
How does this look ?

```
#!/bin/bash
# Ubuntu_Mate 16.04
#    Copy files
#
MINPARAMS=2

echo xxxx | sudo -S cp $1 $2
   
   if [ $# -lt "$MINPARAMS" ]
then
  echo
  echo "This script a needs a filename and a destination!"
fi
```

---

### Post by TheFu on 2017-08-30
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) explains most.  mv and cp are the most basic of Unix commands.

The script looks overly complicated.  You don't need the "echo" part.  Plus never, ever, put the password on a command line. Any userid on the system can look at the process table.  Just modify sudoers to have a longer timeout or specifically allow a command, but be VERY careful doing that w/ cp.  The power to cp is the power to take over the entire system.

cp can use normal file name globbing.

---

### Post by raleigh3 on 2017-08-30
The echo part just lets me know if I do not use 2 parameters.

It is NOT my real password.

And I am the only user.

How does one look at the process table ?

---

### Post by raleigh3 on 2017-08-30
I am the only user of my computer.

How do you look at the process table ?

---

### Post by raleigh3 on 2017-08-30
ps -ef does not show my pw. ?

---

### Post by raleigh3 on 2017-08-31
Things have gotten pretty quiet. ??

---

### Post by wildmanne39 on 2017-08-31
It is probably because of time zones and the fact that this thread is marked solved!

---

### Post by raleigh3 on 2017-08-31
So if it is marked solved, no one reads any further posts ??

---

### Post by wildmanne39 on 2017-08-31
Most of the time that is the case, if it is solved then the person that started the thread no longer has an issue so a lot of people will not look.

Edit:

You can mark the thread unsolved if you want too, also it is normal to wait 12 hours before bumping your thread.

---

### Post by mc4man on 2017-08-31
caja has this already built-in, i.e. Open as Administrator. Can be used on both files & folders. 
Seems alot simpler than anything you've done or are doing & certainly qualifies for 'less typing'

---

