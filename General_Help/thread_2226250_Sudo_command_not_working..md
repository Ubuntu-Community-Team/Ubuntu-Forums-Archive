---
title: "Sudo command not working."
date: 2014-05-26
forum: General Help
---

### Post by mohammad_ali2 on 2014-05-26
Every time I use sudo command it is giving me this error. I was tweaking with the chmod command and this started happening before this sudo was working like a magic.


```
Sudo: /usr/bin/sudo must be owned by uid 0 and have the setuid bit set
```

---

### Post by slickymaster on 2014-05-26
Hi mohammad_ali2, welcome to the forums.

I'm moving your thread from the Server platforms to the **General Help** sub-forum.

To fix your problem with the sudo command just follow this tutorial - [Fix Broken Sudo]("http://www.psychocats.net/ubuntu/fixsudo") - and you should be good to go.

Don't hesitate to post back if you run into any difficulties.

---

### Post by mohammad_ali2 on 2014-05-27
Nah, nothing is working I think I have to reinstall the OS again.

---

### Post by slickymaster on 2014-05-27
Can you please post back the errors you got.

---

### Post by Impavidus on 2014-05-27
This problem may be very easy to solve. The command```
ls -l /usr/bin/sudo
```will tell us what the problem is and how it can be solved from the recovery console.

Also, to make sure this is your only problem, run these commands (copy-past in the terminal):```
ls -la /usr/bin | grep -v "root *root"
ls -la /usr/bin | grep -v "rwxr-xr-x\|^l"
```They should produce only about 15&#8211;25 lines of output each. The first lists all files not owned by root or not in root's group, the second lists all files with special permissions. If you get many more lines of output, your permissions have been completely mixed up. In that case please don't post all of it, a short sample will do.

---

### Post by mohammad_ali2 on 2014-05-28
For the first command this is the output.

```
 -rwxrw--x 1 root root 
```

The output of the second third command is very small its like 5 and 7 lines respectively.

---

### Post by Elfy on 2014-05-28
> **mohammad_ali2 said:**
> The output of the second third command is very small its like 5 and 7 lines respectively.

as people are not psychic and rather than guessing will just go and help someone who does give them the outputs they've asked for - please don't tell us the output is 5 or 7 lines long - but tell us what they are 

run the commands and paste them here as you were asked

---

### Post by mohammad_ali2 on 2014-05-28
Second Command Output:

```
 

drwxw--x 2 ali ali 4096 May 24 11:00 .
-rwxrw-xx 1 ali ali 971 May 25 12:33 .bash_history
-rwxrw-xx 1 ali ali 220 May 25 12:33 .bash_logout
-rwxrw-xx 1 ali ali 3637 May 25 12:33 .bashrc
lrwxrwxrwx 1 ali ali 29 May 23 20:06 .encryptfs -> /home/.encryptfs/ali.encryptfs
lrwxrwxrwx 1 ali ali 28 May 23 20:06 .Private -> /home/.encryptfs/ali.private
-rwxrw--x 1 ali ali 675 May 20:06 . profile

 
```

---

### Post by Bucky Ball on 2014-05-28
Reinstall is generally a last resort and, at this point, a drastic resolution. You are getting good help here, be patient and no doubt we'll get to the bottom of it. ;)

---

### Post by mohammad_ali2 on 2014-05-28
Third Command output:

```
 

drwxrw--x 2 ali ali 4096 May 24 11:00 .
-rwxrw--x 1 ali ali 972 May 25 12:33 .bash
-rwxrw--x 1 ali ali 220 May 23 20:06 .bash_logout
-rwxrw--x 1 ali ali 3637 May 23 20:06 .bashrc
-rwxrw--x 1 ali ali 675 May 23 20:06 .profile


```

Thank you Bucky.

> **Elfy said:**
> as people are not psychic and rather than guessing will just go and help someone who does give them the outputs they've asked for - please don't tell us the output is 5 or 7 lines long - but tell us what they are 

run the commands and paste them here as you were asked

Now I gave all the output let's see if you guys can solve the problem in an efficient manner.

---

### Post by Impavidus on 2014-05-28
Sorry, I made a small error in the second and third command. I copy-pasted them from my terminal where I had checked them, but forgot to mention I had cd'ed to /usr/bin beforehand. I edited my previous post, they should give useful output now.

Your /usr/bin/sudo is owned by root, which is good, but it has lost its set user ID bit. To fix this, follow [these instructions](http://www.psychocats.net/ubuntu/fixsudo) to get a root shell and mount the file system read-write. To do the actual repair, run```
chmod 4755 /usr/bin/sudo
```But I still like to see the result of the other commands. When sudo has lost its setuid bit it's often because the user chmod'ed the whole /usr/bin directory, which means there can be more damage. So this is just to check there are no further and less obvious problems.

---

### Post by mohammad_ali2 on 2014-05-29
Both commands are giving the output 

ls: cannot open directory /usr/bin: Permission denied

Yay! It worked you are great impavidus! Okay, can you explain me a little bit about the mounting the file system read write.

---

### Post by Impavidus on 2014-05-29
The recovery console is meant to fix broken systems, create emergency backups and things like that. When you boot into recovery mode things are often damaged and to prevent further damage the file system is mounted read-only by default. You have to explicitly mount it read-write to fix the system.

But... Permission denied when ls tries to access /usr/bin? How is that possible?
If you cannot read /usr/bin, you could never have got the output from **ls -l /usr/bin/sudo**. And, as I see now, sudo not only lost the setuid bit, but also the other user and the group execute permission bits, but there is also a dash or another character in your output in post #6 missing. That -rwxrw--x should contain 10 characters, not 9.
But if you now cannot read /usr/bin, the permissions of /usr/bin must have changed and it means that you can't do anything when you're not root. So double check that. And check the output of```
ls -ld /usr /usr/bin
```If necessary from the recovery console.

---

### Post by mohammad_ali2 on 2014-05-29
Now it is working with my id also that is ali before it was not working. This is the output for this command.

```


drwxr-xr-x 10 root root 4096 /usr
drwxrw---x 2 root root 20480 /usr/bin


```

And now for the ```
 ls -l /usr/bin/sudo 
``` this output is coming ```
-rwsr-xr-x 1 root root 
``` Now I don't get it what is the s thing in the output.

**ls ld **command is working but only** ls l **command is not working permission problem. The only thing solved is that sudo is working I can get access as root.

---

### Post by Impavidus on 2014-05-29
Right, you have execute permission on /usr/bin for normal users. This means that you can look up inodes from a file name in this directory, so that you can read or execute files in /usr/bin if you know their name, and this is good. However, you don't have read permission for normal users, so you cannot read the directory to list all files present, which is bad. You have to give yourself read permission for this directory. There is write permission for the root group, which should be removed. You can do this all with```
sudo chmod 755 /usr/bin
```

The permissions and owner of /usr/bin/sudo are OK now. The s thing in the output means that the set user ID bit has been set for this file. This means than when you execute sudo, it will be executed with the effective user ID *root*, the owner of the file, instead of your normal user ID, the caller. This allows sudo and therefore you to execute programs with elevated permissions.

The permissions on /usr are OK too.

---

### Post by mohammad_ali2 on 2014-06-01
Thanks for sparing time and explaining so wonderfully you really are a genius. Problem solved.

---

