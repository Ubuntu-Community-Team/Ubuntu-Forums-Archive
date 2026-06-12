---
title: "HELP, weird problem after running WINE !!!!!!!!"
date: 2008-03-05
forum: General Help
---

### Post by parkland on 2008-03-05
Things i've lately done to ubuntu: 

Fooling around with wine.

Trying to change "home" folder settings for read/write access cause wine says it cant write in one of those folders.

Changed the loader screen, so it boots up without a username or passwd. 


Now, when i turn it on, it start to boot, then i see 

"User's $HOME/.dmrc file is being ignored. This prevents the session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by others."

So i click OK, and then....


"Your session lasted less than 10 seconds. ....there may be an installation problem......" goes on about disk space (not the problem)...

Then, when i click on "veiw details", heres what i get...


Gtk-WARNING
Another Gtk warning, 

And a GTK initialization problem because :

Cant create dir /home/user/desktop
cant create dir /home/user/templates
cant rcreate dir /home/user/music

and on and on like this......
:(

Then, 
X-session manager 
could not create per user Gnome configuration directory /home/user/.gnome2/ permission denied

:confused:

What the heck?!?!?!?!?!

Ubuntu has been good till this...   What have i done to my 'puter?


Any help GREATLY APPRECIATED!!!!:confused:

---

### Post by Rocket2DMn on 2008-03-05
When fiddling with the permissions on your home folder, you screwed something up.
Do CTRL+ALT+F1 to get to a tty if you're not already at one.
```
sudo chown -R [yourusername] /home/[yourusername]
chmod 644 ~/.dmrc
```
What commands did you already run before you had the problem?
Try booting the GUI now:
```
startx
```

---

### Post by parkland on 2008-03-05
Chown: missing operand after '/home/user'

---

### Post by Rocket2DMn on 2008-03-05
> **parkland said:**
> Chown: missing operand after '/home/user'

haha my bad
```
sudo chown -R [yourusername] /home/[yourusername]
chmod 644 ~/.dmrc
```
I'll fix my original post, too.

---

### Post by danwood76 on 2008-03-05
it should be:
```

sudo chown -R [yourusername]:[yourusername] /home/[yourusername]

```
to re own your home folder.

-- edit --
beat me to it!

---

### Post by parkland on 2008-03-05
I'm telling her "chmod 644 ~/.dmrc"

And then she said:

"   '//.dmrc' : no such file or directory"

---

### Post by danwood76 on 2008-03-05
try:
```
chmod 644 /home/[yourusername]/.dmrc

```

---

### Post by parkland on 2008-03-05
"cannot access '/home/user/.darc' : no such file or directory"

:confused:

---

### Post by Rocket2DMn on 2008-03-05
"chmod 644 /home/[yourusername]/.dmrc" 
as danwood76 said, should do it. 

There is no .darc file.

 The "~" is short for /home/username but only works if you're logged into that user, which I guess you're not...
Try logging in normally now, does it work OK?

---

### Post by parkland on 2008-03-05
I tries "SUDO CHMOD....

it seemed to work, i'm restarting now to see if its fixed....

---

### Post by danwood76 on 2008-03-05
Just re read your original post.
Is your home directory still there?

to check:
```

cd /home
ls -l

```

---

### Post by parkland on 2008-03-05
I'm running those commands, and they arent giving me any errors, but still wont start up proper...

Sill givin me the same error messages on startup...

---

### Post by parkland on 2008-03-05
Dont know if this is right, 

In terminal, i log in as user, which is my account.

cd home, ok
cd user, permission denied. 

shouldnt i be able to get in there?

I'm trying to find the recycle folder, to see if theres any folders accidentally deleted...

---

### Post by danwood76 on 2008-03-05
what is the output of:
```

cd /home
sudo ls -l

```
it wont give an error but will show what user directories there are and the permissions.
If you have done an accidental rm it doesnt go to the wastebasket but is gone.

---

### Post by Rocket2DMn on 2008-03-05
I think it would be beneficial to have more details on what you actually did before the problem started.  Do you remember any commands you ran and what files/directories you ran them on?

If it won't let you access your home directory, it means you don't own it, which means you didn't run the chown command?
```
sudo chown -R *yourusename* /home/*yourusername*
```

The "ls -l" command above should show us.

---

### Post by parkland on 2008-03-05
drw-rw-rw- 54 user user 4096 2008-03-05 03:08 user

---

### Post by danwood76 on 2008-03-05
what is the output of:
```

cd /home/user
ls -al

```
there should be quite a few directories with you as owner.

---

### Post by parkland on 2008-03-05
I was running wine, and trying to install "flight simulator 2004", and i was moving lots of files, uninstalling other junk, i probably accidentally did something, and the problem didnt show till next startup!

My fault, oh boy...

---

### Post by Rocket2DMn on 2008-03-05
That looks right... why don't you reboot and try again.
Just to double check something, can you post:
```
$HOME
```

---

### Post by parkland on 2008-03-05
I cant got to "user", says "permission denied"

when i type $HOME, says -bash: /: is a directory

---

### Post by Rocket2DMn on 2008-03-05
> **parkland said:**
> I cant got to "user", says "permission denied"

when i type $HOME, says -bash: /: is a directory

LOL that is bad.  Your home directory got changed to the root of the filesystem - how did you pull that off?  Let's set it back to normal:
You mist reboot into recovery kernel so that you are logged out - then run:
```
usermod -d /home/user user
```
Then reboot
```
reboot
```

---

### Post by parkland on 2008-03-05
recovery, i assume restart computer and in the boot loader, go to "recovery mode" ???

(Apologizing for slow, or erratic responses, using mother in law's 500mhz 128mb windows pc, with so much spyware that i can barely read your instructions before browser closes again.)


OK done, but still the same problem, when i entered the command, it just went to the next line, no pause, no error, no nothing. mabye i didnt do it right?....

---

### Post by Rocket2DMn on 2008-03-05
That is correct.  After running that command, just type out "reboot" and choose the normal kernel.

---

### Post by parkland on 2008-03-05
Should i try again, and then try the CHMOD, and other command again ???


Still the same errors on startup!

---

### Post by Rocket2DMn on 2008-03-05
Show me $HOME again, and go ahead and try the chown and chmod commands again, but I don't think they will help much.  The chown command must come first with the -R option.
I have to go for a few hours, but I'll be back to check up on you later.  Good luck.

---

### Post by parkland on 2008-03-05
-bash: /: is a directory


Also , just noticed that when entering terminal, it says 

"No directory, logging in with HOME=/"


Thanks so much for all your help see you later!!!






still same problem

---

### Post by Rocket2DMn on 2008-03-05
OK, are you sure you ran that usermod command correctly?  Maybe "user" is just a bad name.  You may want to consider creating a new login for yourself, you can do it with the "adduser" command - see the man page: [http://linux.die.net/man/8/adduser](http://linux.die.net/man/8/adduser)
You will also have to add this new user to the "admin" group as well as some others possibly, so that you can use sudo with that username (may even have to manually edit /etc/sudoers).  Ask about this if you need help, but I gtg right now, so good luck!

---

