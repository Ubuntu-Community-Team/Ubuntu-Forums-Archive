---
title: "Wall command not working in Lubuntu 15.10"
date: 2016-03-10
forum: General Help
---

### Post by Rooster2000 on 2016-03-10
The following post is moved from [this]("http://ubuntuforums.org/showthread.php?t=2306429&page=2&p=13447804#post13447804") thread.

--

I have tried now few Lubuntu and one Ubuntu Live installers with following results:

[TABLE="class: grid, width: 500"]
[TR]
[TD]**File**[/TD]
[TD]**Wall command working**[/TD]
[/TR]
[TR]
[TD]lubuntu-14.04.3-desktop-i386.iso[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]lubuntu-15.10-desktop-i386.iso[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]lubuntu-15.10-desktop-amd64.iso[/TD]
[TD]No[/TD]
[/TR]
[TR]
[TD]ubuntu-15.10-desktop-i386.iso[/TD]
[TD]Yes[/TD]
[/TR]
[/TABLE]


The md5sum of each file was checked before extracting them with  UNetbootin to USB stick, and file integrity was tested before starting  Live.
The command I used to test if wall works properly:

```
sudo echo "Testing" | wall
```

And this was expected to produce a system message to terminal. For both  Lubuntu 15.10 versions, this didn't cause any feedback, which is the  case in my current 15.10 (Lubuntu) system too. Also, no error message is  displayed when typed:

```
 sudo wall "Testing"
```

Why is wall command not working in Lubuntu 15.10? Is this a bug in  installer files? Can anyone get wall command to work properly in Lubuntu  15.10?

---

### Post by him610 on 2016-03-10
I know you did not ask for this, but it works for...	
Ubuntu 14.04.4 LTS
3.16.0-62-generic #83~14.04.1-Ubuntu SMP Fri Feb 26 22:52:39 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Maybe you should consider a fallback to 14.04.4 if you want it to work, or wait for 16.04.

---

### Post by mcgess on 2016-03-10
Hi, I'm not sure why wall is not working for you but there is a problem with one of your commands

```
sudo echo "Testing" | wall
```

In this example the sudo applies only to the _echo "Testing"_ bit, after the pipe command wall would be run as the normal user.

```
echo "Testing" | sudo wall
```

will run wall with elevated privileges.

Martin

---

### Post by Rooster2000 on 2016-03-11
> **hgh9mrp said:**
> Maybe you should consider a fallback to 14.04.4 if you want it to work, or wait for 16.04.

The reason I moved from Lubuntu 14.04.3 LTS - where shutdown notifications and wall command worked properly - to 15.10, was that it didn't have support for my new motherboard's ethernet device (Intel Corporation Device 15b8 (rev 31), see [this]("http://ubuntuforums.org/showthread.php?t=2305909&p=13404645#post13404645") thread). Otherwise I would have waited for the 16.04 LTS. As it is only month away, I guess I'll wait for it with this case too.

--

> **mcgess said:**
> there is a problem with one of your commands

```
sudo echo "Testing" | wall
```

In this example the sudo applies only to the _echo "Testing"_ bit, after the pipe command wall would be run as the normal user.

```
echo "Testing" | sudo wall
```

will run wall with elevated privileges.

Hmm, are you sure? This command succeeded normally in those Live -installers and also in my 14.04.3 LTS.

---

### Post by mcgess on 2016-03-11
Fairly certain. Here's a quick check of sudo use with piped output using the tee -a command instead of wall as it is easier to show

```

martin@C660D:~$ touch zzz.txt
martin@C660D:~$ echo "testing 1" | tee -a zzz.txt
testing 1
martin@C660D:~$ cat zzz.txt 
testing 1
martin@C660D:~$ chmod -w zzz.txt 
martin@C660D:~$ echo "testing 2" | tee -a zzz.txt
tee: zzz.txt: Permission denied
testing 2
martin@C660D:~$ cat zzz.txt 
testing 1
martin@C660D:~$ sudo echo "testing 3" | tee -a zzz.txt
tee: zzz.txt: Permission denied
testing 3
martin@C660D:~$ cat zzz.txt 
testing 1
martin@C660D:~$ echo "testing 4" | sudo tee -a zzz.txt
testing 4
martin@C660D:~$ cat zzz.txt 
testing 1
testing 4
martin@C660D:~$ 

```

I don't know the wall command but from a quick search I think that wall can only write to users who allow access, with sudo wall will write message to all users.

Martin

---

### Post by Rooster2000 on 2016-03-12
> **mcgess said:**
> I don't know the wall command but from a quick search I think that wall can only write to users who allow access, with sudo wall will write message to all users.

Yes, that would explain why it seemed to work correctly on the terminal. Thanks for the correction.

---

### Post by Rooster2000 on 2016-03-21
Well, I'll mark this thread as solved as I decided to wait Ubuntu 16.04 LTS.

Would have been interesting to know though if it was just me.

---

