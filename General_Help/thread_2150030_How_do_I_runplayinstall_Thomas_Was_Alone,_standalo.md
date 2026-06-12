---
title: "How do I run/play/install Thomas Was Alone, standalone version, from Humble Bundle?"
date: 2013-05-30
forum: General Help
---

### Post by hanzj on 2013-05-30
Hi, community.

I bought and downloaded Thomas was alone (the standalone version) for linux. I've extracted the .rar file. There are 2 main parts. 

```
 $ ls
thomasWasAlone  thomasWasAlone_Data

```

According to "Properties", thomaswasAlone is 
"Type: executiable (application/x-executable).

>  $ ls -l
-rwxr-xr-x 1 main main 15479748 May 17 09:14 thomasWasAlone


> ./thomasWasAlone
bash: ./thomasWasAlone: No such file or directory

Why does it say "No such file"? It's right there.

How do I execute it?

---

### Post by Dennis N on 2013-05-30
> **hanzj said:**
> Hi, community.

I bought and downloaded Thomas was alone (the standalone version) for linux. I've extracted the .rar file. There are 2 main parts. 

```
 $ ls
thomasWasAlone  thomasWasAlone_Data

```

According to "Properties", thomaswasAlone is 
"Type: executiable (application/x-executable).

Why does it say "No such file"? It's right there.

How do I execute it?

First, change the permissions on the executable: **chmod +x thomasWasAlone**
Then, either:

1) If you are using the terminal,
cd to the folder **thomasLinuxStandalone**
to start the game, type **./thomasWasAlone**

2) You can just double click on the executable in the file manager and it will start up.


(I have an annoying tooltip with white background about the controls always displaying - if you know how to disable this, let me know here. I could find no way.)

---

### Post by hanzj on 2013-05-30
Hi, DennisN,
I did what you instructed in "1." I've already pasted the outcome in my original post.

---

### Post by Sizza147 on 2013-05-31
Had the exact same problem, solution worked fine for me. 
Make sure you 'cd' to the right location.

cd /home/NAME/Documents/thomasLinuxStandalone

...and then 

./thomasWasAlone

---

### Post by Dennis N on 2013-05-31
> **hanzj said:**
> Hi, DennisN,
I did what you instructed in "1." I've already pasted the outcome in my original post.

The only thing that comes to mind is that you have not changed your working directory to the one containing the program files. Here are the command and output from terminal when starting the game. I place all downloaded games like these (no .deb available) in ~/games.

```
dn@Kayleigh:~/games/thomasLinuxStandalone$ ./thomasWasAlone
Set current directory to /home/dn/games/thomasLinuxStandalone
Found path: /home/dn/games/thomasLinuxStandalone/thomasWasAlone
Mono path[0] = '/home/dn/games/thomasLinuxStandalone/thomasWasAlone_Data/Managed'
Mono path[1] = '/home/dn/games/thomasLinuxStandalone/thomasWasAlone_Data/Mono'
Mono config path = '/home/dn/games/thomasLinuxStandalone/thomasWasAlone_Data/Mono/etc'

```
and now the game is running.

In the terminal, you can use the full path starting from / and this will also start it:

```
dn@Kayleigh:~$ /home/dn/games/thomasLinuxStandalone/thomasWasAlone
```

You can also start your file manager and double-click on the executable 

On the other issue I raised on the tooltip:

> (I have an annoying tooltip with white background about the controls always displaying - if you know how to disable this, let me know here. I could find no way.) 


I installed on another computer, and same result. Screenshot attached. Do you have this also? If you figure out how to disable, please post back. Google led me to no answer (yet).

Thanks.

---

### Post by Sizza147 on 2013-05-31
Tooltip, is as far as I can tell - part of the game itself. Goes away after a few levels. (Maybe a set period of time)

---

### Post by Dennis N on 2013-05-31
> **Sizza147 said:**
> Tooltip, is as far as I can tell - part of the game itself. Goes away after a few levels. (Maybe a set period of time)

Thanks for the reply. Just the first couple of screens would be enough. Since it's going to go away, I will give it another go.

---

### Post by hanzj on 2013-05-31
Hmmmm.... Still doesn't work for me. I even let Terminal autocomplete the folders and the executable.

UPDATE: I guess I could just download the Windows version and play on Windows.

---

### Post by Dennis N on 2013-05-31
Can't tell why yours is not going,  but there is a reason for sure. It is just not yet apparent. Did you try the other suggested ways to start Thomas?

1) In the terminal, you can use the full path to the program starting from root (/) of the filesystem and this will start it:

example:

<user>@computer-name:~$ /home/<user>/<rest of path to thomasLinuxStandalone directory>/thomasLinuxStandalone/thomasWasAlone

2) You can also start your file manager, and double-click on the program executable.

--------------------------------------

---

### Post by closethipster on 2013-06-12
Are you on a 64-bit system? I had the same problem. Installing ia32-libs-multiarch:i386 fixed it.

The only other thing that caught me up (in game): to select an item from the menus, use the spacebar.

Hope this helps.

---

### Post by hanzj on 2013-06-12
Dennis, I just gave up. It's just a game. I have work to do.  So I don't feel bad.

---

### Post by hanzj on 2013-06-12
Yes, am on 64-bit system. But I won't be trying to make this game work. I have much work to do. Thank you, closethipster, for your reply, though.

---

