---
title: "Update Error"
date: 2007-02-02
forum: General Help
---

### Post by flyking on 2007-02-02
Whenever I try to update Ubuntu Dapper via Update Manager, Apt command line, or any other method, I always get the following error message:

"Only one software management tool is allowed to run at the same time

Please close the other application e.g. 'aptitude' or 'Synaptic' first."

I get the following error message when I try to open the Synaptic Package Manager:

"Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first."

I'm not sure what I'm supposed too close because I can't find any open applications.


Can this problem be fixed?


Regards,

George

---

### Post by 23meg on 2007-02-02
Are you sure you're not running apt-get or aptitude to install something when trying to update?

---

### Post by flyking on 2007-02-02
As far as I can see all Workspaces and ongoing processes are closed.  Nothing is showing open.  

Is there a way to force all update processes closed?

Thank You for your prompt reply.


Regards.

George

---

### Post by flyking on 2007-02-03
I guess I might as well accept the fact that my Ubuntu install is basically broken and I'm probably not going to get any help fixing it.  It could be that i'm the only one out here having these issues.

---

### Post by flyking on 2007-02-05
Bump.

Thought I'd try again.

---

### Post by teaker1s on 2007-02-05
look at the thread below the problem packages listed will be different, but process the same
[http://www.ubuntuforums.org/showthread.php?t=187765]("http://www.ubuntuforums.org/showthread.php?t=187765")

---

### Post by gargo2000 on 2007-02-14
I am having the same problem.  The icon popped up stating theres updates, so I click update and some were not able to update.  It asked me to reboot which I did and once back up and running, The icon stated there were more updates.  I went to click on it and it comes up with the same error stated above, "Only one software management tool is allowed to run at the same time.  Please close other application e.g. 'aptitude' or 'Synaptic' first."  Now I just rebooted and I know I didn't load anything.

Any ideas?

Tanner

---

### Post by flyking on 2007-02-14
Thanks for replying to my post.  I'm sorry to hear that you're having the same problem that I was experiencing.  I wish I could help you out with it.  I tried everything I could think of to fix the update problems I was having.  I got very few responses to my post and after trying everything I could think of I finally gave up.  I ended up completely uninstalling Ubuntu and I've been using Windows XP since.

My experience so far is that I've had allot more success  getting  help with my windows problems than I have with my Ubuntu problems.


Kindest Regards,

George

---

### Post by bapoumba on 2007-02-15
Hum ...
May be a problem with the lock file. 
```
~ $ ls -la /var/cache/apt/archives/lock
-rw-r----- 1 root root 0 2007-02-11 22:44 /var/cache/apt/archives/lock

```

---

### Post by jagannath on 2007-03-11
> **bapoumba said:**
> Hum ...
May be a problem with the lock file. 
```
~ $ ls -la /var/cache/apt/archives/lock
-rw-r----- 1 root root 0 2007-02-11 22:44 /var/cache/apt/archives/lock

```

Well. I'm another of those guys with this identical problem.
Tried the code you had given and got the response you had indicated. But the same error message persists.  Hope I'd get some more help to  'close aptitude or suynaptic'](*,)

---

### Post by bapoumba on 2007-03-11
@ jagannath: try to rename the lock file, another one will be created if necessary.
```
sudo mv /var/cache/apt/archives/lock /var/cache/apt/archives/lock_bak
```

---

### Post by jagannath on 2007-03-11
Thanks, bapoumba.

J

---

### Post by tguinn on 2007-12-07
this fixed the error for me:

type in terminal:

   dpkg --configure -a

apparent;y an earlier install of google earth had not completed - I discovered the fix typine apt-get update  in terminal error was discovered and the "fix" was to try dpkg --configure -a
hope this helps - I know it is a bit late but just re-created your problem 

                           penguin

---

