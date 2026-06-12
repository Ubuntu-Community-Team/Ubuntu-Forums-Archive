---
title: "Ubuntu 10.04  no valid sudoers source found"
date: 2012-11-08
forum: General Help
---

### Post by Dr_Lion on 2012-11-08
I am trying to fix this problem for two hours and nothing, i tried some comands that i saw on the net,   the chmod 0440  /etc/sudoers  nothing.

I create another user, i can log in  my users, but i can't get sudo because de error, and i don't have  su

i can't mount a pen because i need the sudo that i don't have.

my system is ubuntu 10.04 lts

the error says: 

>>> /etc/sudoers: /etc/sudoers.d near line 24 <<< sudo: parse error in /etc/sudoers near line 24 sudo: no valid sudoers sources found, quittin
all my tries were in the sudoers file, however it says the error is in "sudoers.d" so do you have any sugestion to what i can try in sudoers.d??

if i enter in the recovery mode i can't log as sudo, but i thing i'm allready as sudo so i may try in last resource to use that way to copy something to the pendrive.


Thanks in advance and sorry mi bad inglish.

---

### Post by drmrgd on 2012-11-08
Not sure what commands you've followed from the net so far.  If you've not followed this guide, though, I think this could benefit you:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

The other common problem that's not mentioned in that guide is if the ownership of the sudoers file has been changed inadvertently.  You might check to be sure that root owns it (just setting 440 permissions isn't enough in the case where root does not own it - you need to have both conditions met).  Have a look at this thread for more details:

[http://ubuntuforums.org/showthread.php?t=1923285](http://ubuntuforums.org/showthread.php?t=1923285)

Finally, you said you can't log in as sudo from recovery mode.  Do you mean you can't drop to a root shell prompt?  You don't log in as sudo, and I'm not sure if you might be trying to do it incorrectly or not.  Follow the Psychocats tutorial for dropping to a root shell.

---

### Post by Dr_Lion on 2012-11-08
> **drmrgd said:**
> Not sure what commands you've followed from the net so far.  If you've not followed this guide, though, I think this could benefit you:

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

The other common problem that's not mentioned in that guide is if the ownership of the sudoers file has been changed inadvertently.  You might check to be sure that root owns it (just setting 440 permissions isn't enough in the case where root does not own it - you need to have both conditions met).  Have a look at this thread for more details:

[http://ubuntuforums.org/showthread.php?t=1923285](http://ubuntuforums.org/showthread.php?t=1923285)

Finally, you said you can't log in as sudo from recovery mode.  Do you mean you can't drop to a root shell prompt?  You don't log in as sudo, and I'm not sure if you might be trying to do it incorrectly or not.  Follow the Psychocats tutorial for dropping to a root shell.

I tried the 1º case and it said that i was already in admin group.
The first link you say is exactly the one i followed. tried the 2º cases and it did not solved my problem. 

But in the file i tried with this kind of sintax:

root	ALL=(ALL) ALL

and not the next one that says in the example:

root	ALL=(ALL:ALL) ALL 

anyway my other pc has the first sintax and it works, so i supose it is not because of that, but now i will try with teh ALL:ALL .

I also tried to add another user, but not a admin user. same problem, 

Now i found a maybe strange situation, i don't have sudoers.d directory, can be that the problem? comparing to the pc from where i'm writing with ubuntu 10.04 also, here i have the /sudoers.d but i did a ls -la, and i only see 3 entries:    
  .    
  ..    
  README  

so the lack of this directory can be causing the problem or not? since i don't see any "usefull" file in here??

The second link you talk about, i did
chown root:root /etc/sudoers

 but when i tried the 
pkexec chmod 0440 /etc/sudoersi got a segmentation fault :( but i don't understand very well when you talk about root owns it, i'm not so sure if it owns it. how can i see it?

The last paragraph forget, and yes i can drop the root shell, it is what i'm using to try the above links.

---

### Post by drmrgd on 2012-11-08
I don't think it's the root line that's wrong in your file, based on the error.  At least in my file, which is a standard file, it's the 'sudo' section, which reads like this in mine:

```
%sudo ALL=(ALL) ALL
```

Can you verify that you have exactly the same thing (even capitalization is important here)?

Also, by ownership I mean actually the system user account that owns the file.  You can see this when you run 'ls -l' on that file.  For example:

```
-r--r----- 1 root root 723 Jan 31  2012 /etc/sudoers
```

If you do that, you should get exactly the same results as I did.

I'm not entirely sure about sudoers.d.  I have that directory, and it looks the same as you describe (only a README file).  Did a quick search and learned that the file:

> sudo will read each file in /etc/sudoers.d, skipping file names that end in ~ or contain a . character to avoid causing problems with package manager or editor temporary/backup files. Files are parsed in sorted lexical order. That is, /etc/sudoers.d/01_first will be parsed before /etc/sudoers.d/10_second. Be aware that because the sorting is lexical, not numeric, /etc/sudoers.d/1_whoops would be loaded after /etc/sudoers.d/10_second. Using a consistent number of leading zeroes in the file names can be used to avoid such problems.

I'm not sure if it's related to your problem or not, though.  I wouldn't imagine this is what's causing the issue, but I could be wrong.  You could try to create one and see what happens.  You should be able to do that from the root shell:

```
mkdir /etc/sudoers.d
```

Then verify the permissions are correct:

```
chmod 755 sudoers.d
```

My sudoers file looks just like the psychocats tutorial  Here's the copy from my server, though, which is also 10.04 (I've excluded the extra entries in there, I hope):

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults        env_reset

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Allow members of group sudo to execute any command after they have
# provided their password
# (Note that later entries override this, so you might need to move
# it further down)
%sudo ALL=(ALL) ALL
#
#includedir /etc/sudoers.d

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

---

### Post by Dr_Lion on 2012-11-08
Everything is like you say, and i  created the folder, but the permitions are:

drwxr-xr-x 2 root root 4096 "data" /etc/sudoers.d
because i did not specify any permitions.

Anyway i think i willl choose the reinstall option, because i have other issues like the pendrive is not mounted automatically and i have some process runing that does not let the pc shutdown, it logs of instead, and i have to shut it down in the console with the shutdown comand.. and as i don't have it now, every time i do it, i have to do the recovery with de cd :(

---

### Post by drmrgd on 2012-11-08
Hmmm...I hate to give up and reinstall, but given what you've just said, it may be best.  You may have some other things going on there that are not ideal.  Sorry to not have been more help

---

