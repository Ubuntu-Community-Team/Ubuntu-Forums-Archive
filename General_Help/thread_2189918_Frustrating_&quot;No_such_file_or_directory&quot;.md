---
title: "Frustrating: &quot;No such file or directory&quot;"
date: 2013-11-24
forum: General Help
---

### Post by james.bianchi on 2013-11-24
Hello all,

I am running Ubuntu 12.04 on my dedicated and accessing via x2go

I am new to Linux but something isn't right with what is going on with my system. I will create a new folder and the system won't recognize it.. At all.. This also happens with all my files that I drag to a folder (even pre existing) it will not recognize the files.

Example:

created a folder named 'hello' in /home
try to access it via terminal

```
desktop@ks4005552:~$ cd /home/hello
bash: cd: /home/hello: No such file or directory
desktop@ks4005552:~$

```
Note: that I go to my home directory and I can physically see the folder 'hello'

I then go to give it full access as maybe that's the problem:

```
desktop@ks4005552:/home$ sudo chmod 777 -R hello
chmod: cannot access `hello': No such file or directory
desktop@ks4005552:/home$
```

I've tried this both with and without sudo, still nothing.

This is extremely frustrating because I really can't do anything with new folders or files. Any input would be greatly appreciated. Thank you!!!!

---

### Post by grahammechanical on 2013-11-24
Try using this form of the command

```
cd /home/your user name/hello
```

If you run this command you will see the folders in /home

cd /home[/code]

```
ls
```

There should only be one with your user name. Unless there are other users.

Regards.

---

### Post by Dennis N on 2013-11-24
If you made the new folder **hello** in your home directory, the path to it would be **/home/<username>/hello** and not **/home/hello**.

---

### Post by steeldriver on 2013-11-24
I think you may be confused by what the GUI file manager calls 'Home' and the system directory /home

In *nix, /home is a directory *containing* the home directories (as indicated by the value of each user's $HOME environment variable). So for example, if I am logged in as steeldriver then in a terminal

 ```

$ echo $HOME
/home/steeldriver

```

Any files/directories that I create as *steeldriver* in the 'Home' directory of the GUI file manager (i.e. the directory with default subdirectories 'Downloads', 'Documents', 'Music' and so on) go in **this** directory - **not** in the parent system directory /home where you're looking for them - assuming your login name is 'desktop' (as indicated by your terminal prompt) will probably find that

```

cd /home/**desktop**/hello

```

works. You can also use the shorthand ~ to mean the logged-in user's $HOME dir, i.e.

```

cd **~/**hello

```

---

### Post by drmrgd on 2013-11-24
Are you sure you're looking in the correct place for it?  Your home directory is actually a subdirectory under /home (e.g. /home/james.bianchi/).  But you're saying that you've put the new directory in /home instead (i.e. /home/hello/).  So, is your directory structure like this:

```

/home/hello

```

or like this 
```

/home/<username>/hello

```

You might check by running:

```

ls -l

```
in both /home and /home/<username>

You should also note that /home itself is owned by root, so you need to use sudo to add a new directory to /home, but you own your own home directory and won't need to elevate privileges to make the directory and shouldn't need to set the permission of the directory to '777' to access / read / write / etc in that directory

**EDIT**: Wow I type slowly!  Got scooped by several others!

---

### Post by deadflowr on 2013-11-24
If the path your in is the default ( ~) then simply type cd hello, no need to use the full path.
```
cd hello
```

---

### Post by james.bianchi on 2013-11-24
Thank all you guys. I read everyone's posts and everything makes a lot more sense now. This saved me from so much more frustration, thank you!

---

