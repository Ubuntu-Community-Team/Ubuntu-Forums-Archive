---
title: "need help withsystem ownership"
date: 2008-07-03
forum: General Help
---

### Post by chillyair on 2008-07-03
OK I am having a difficult time with file ownership. Whenever I try to add something to a program file in usr/lib/ I get a popup that says I cant do it because I dont have permission. Looking at the permissions tab of these program files it says the owner is root. I am currently operating under the user james. I am the only one who uses this computer or ever has. What do I do to give myself full access to my computer?

---

### Post by spiderbatdad on 2008-07-03
you can run the command ```
gksu nautilus
```for a gui file browser/editor in admin mode.

or use appropriate cp mv commands from the terminal with sudo...sudo cp home/james/some/file usr/lib

---

### Post by sisco311 on 2008-07-03
READ THIS:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

nautilus is the default file manager in Ubuntu.
You can open nautilus as root from a terminal:
```
gksu nautilus
```

---

### Post by chillyair on 2008-07-03
ok tried gksu nautilus and this is what came up


Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:7164): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown



what do I do now?

---

### Post by AnarkistNZ on 2008-07-03
Try this

1) Open terminal
2) Type 'sudo -s'
3) Enter the passwd for your username
4) Use the 'mv' (move) or 'cp' (copy) commands.

Alternatively, you can change the permissions on that directory using the 'chmod' command through terminal.

For more information on the above commands, as well as valid arguments when using them type 'man cp' 'man mv' or 'man chmod'

---

### Post by chillyair on 2008-07-03
> **AnarkistNZ said:**
> Try this

1) Open terminal
2) Type 'sudo -s'
3) Enter the passwd for your username
4) Use the 'mv' (move) or 'cp' (copy) commands.

Alternatively, you can change the permissions on that directory using the 'chmod' command through terminal.

For more information on the above commands, as well as valid arguments when using them type 'man cp' 'man mv' or 'man chmod'

Could you be a little more specific about using the mv and cp commands? I'm very new to linux and haven't gotten alot of experience with the command line yet.
Thanks

---

### Post by cariboo on 2008-07-03
How about open a terminal and enter:

```
man cp
```

and

```
man mv
```

Jim

---

### Post by chillyair on 2008-07-03
> **cariboo907 said:**
> How about open a terminal and enter:

```
man cp
```

and

```
man mv
```

Jim

Right, OK.   But like I said i'm new to linux. How do I use these to solve my issues regarding permissions and nautilus.

---

### Post by AnarkistNZ on 2008-07-03
> **chillyair said:**
> Right, OK.   But like I said i'm new to linux. How do I use these to solve my issues regarding permissions and nautilus.

Can you be a little more descriptive about the issue you're having?

Exactly what you're trying to achieve, and the error messages you're getting would be a great start in helping us tell what the issue is.

---

### Post by chillyair on 2008-07-03
> **AnarkistNZ said:**
> Can you be a little more descriptive about the issue you're having?

Exactly what you're trying to achieve, and the error messages you're getting would be a great start in helping us tell what the issue is.

Sure sorry I wasn't exactly clear to begin with. Basically I downloaded a new theme for cinelerra. part of the installation instructions were to move the extracted files into the usr/lib/cinelerra directory. However when I tried to do this a message popped up saying

Error while moving "monkeytheme.so".
There was an error moving the file into /usr/lib.
Error moving file: Permission denied

I've attached a screenshot also so you can see
Hope this clears things up

---

### Post by AnarkistNZ on 2008-07-03
I don't have alot of experience using GUI's on Linux so I don't have any idea how you'd copy as a superuser via GUI, however I suggest you try this via command line:

1) Open terminal
2) Type 'sudo -s'
3) Enter the passwd for your username
4) Type 'cd /home/james/Desktop/mon' (Press tab and it will auto-complete the directory name)

(You want to navigate to the directory that the files you're wanting to move are in)

5) Type 'mv <file names here> <destination>'

e.g. 'mv myfile.txt /home/james/destinationfolder/'
or
e.g. 'mv /home/james/myfolder /home/james/Desktop/destinationfolder'

(Again, use the 'tab' key to auto complete folder names)

---

### Post by bodhi.zazen on 2008-07-03
cp = copy

mv = move

These links may help :

	[http://linuxcommand.org/](http://linuxcommand.org/)

[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)

---

### Post by chillyair on 2008-07-03
> **AnarkistNZ said:**
> I don't have alot of experience using GUI's on Linux so I don't have any idea how you'd copy as a superuser via GUI, however I suggest you try this via command line:

1) Open terminal
2) Type 'sudo -s'
3) Enter the passwd for your username
4) Type 'cd /home/james/Desktop/mon' (Press tab and it will auto-complete the directory name)

(You want to navigate to the directory that the files you're wanting to move are in)

5) Type 'mv <file names here> <destination>'

e.g. 'mv myfile.txt /home/james/destinationfolder/'
or
e.g. 'mv /home/james/myfolder /home/james/Desktop/destinationfolder'

(Again, use the 'tab' key to auto complete folder names)

Well that worked thanks. I learned a little more about the command line too. But just out of curiosity, is there anyone who knows why I cant simply drag and drop?

---

### Post by AnarkistNZ on 2008-07-03
> **chillyair said:**
> Well that worked thanks. I learned a little more about the command line too. But just out of curiosity, is there anyone who knows why I cant simply drag and drop?

Because the permissions on the destination directory aren't set to allow you (more specifically, the user you're currently authenticated as) write access to them.

---

### Post by bodhi.zazen on 2008-07-03
> **AnarkistNZ said:**
> I don't have alot of experience using GUI's on Linux so I don't have any idea how you'd copy as a superuser via GUI, however I suggest you try this via command line:

1) Open terminal
2) Type 'sudo -s'
3) Enter the passwd for your username
4) Type 'cd /home/james/Desktop/mon' (Press tab and it will auto-complete the directory name)

(You want to navigate to the directory that the files you're wanting to move are in)

5) Type 'mv <file names here> <destination>'

e.g. 'mv myfile.txt /home/james/destinationfolder/'
or
e.g. 'mv /home/james/myfolder /home/james/Desktop/destinationfolder'

(Again, use the 'tab' key to auto complete folder names)

Consider using sudo -i (sudo -i uses root's environmental variables)

> **chillyair said:**
> Well that worked thanks. I learned a little more about the command line too. But just out of curiosity, is there anyone who knows why I cant simply drag and drop?

Normally you can drag and drop with nautilus. Otherwise see what AnarkistNZ advised re: permissions. 

Finally, gksu nautilus then allows you to drag and drop (so you do not *need* to use the command line).

---

### Post by chillyair on 2008-07-03
[QUOTENormally you can drag and drop with nautilus. Otherwise see what AnarkistNZ advised re: permissions. 

Finally, gksu nautilus then allows you to drag and drop (so you do not *need* to use the command line).[/QUOTE]

I had problems trying to run nautilus as i mentioned a little earlier in this thread. This is what I get when I try to run gksu nautilus.


"Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:7164): WARNING **: Unable to add monitor: Operation not supported
seahorse nautilus module shutdown"




Any ideas on whats wrong?

---

### Post by bodhi.zazen on 2008-07-03
My guess is either you are trying to share a directory you do not have permission to access or the permissions of /var/lib/samba/usershares are wrong.

---

### Post by chillyair on 2008-07-03
> **bodhi.zazen said:**
> My guess is either you are trying to share a directory you do not have permission to access or the permissions of /var/lib/samba/usershares are wrong.

uhhh, OK.   CAn you suggest a way to fix this?

Thanks

---

### Post by bodhi.zazen on 2008-07-04
Not without additional information. What sharing are you doing ? what directory are you sharing or mounting ? is your computer a server or client ?

here are some links on permissions :

[http://www.zzee.com/solutions/linux-permissions.shtml](http://www.zzee.com/solutions/linux-permissions.shtml)



[uhelp]community/FilePermissions[/uhelp]

You can not share a directory if you do not have permission to read and execute it. You need write permissions to share rw.

Do not share your home directory :)

If you are running a samba server you can stop samba with :

```
sudo /etc/init.d/samba stop
```

---

