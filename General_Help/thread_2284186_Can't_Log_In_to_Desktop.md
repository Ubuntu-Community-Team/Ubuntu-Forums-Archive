---
title: "Can't Log In to Desktop"
date: 2015-06-27
forum: General Help
---

### Post by Tk007LwZFJW5ej on 2015-06-27
I have Ubuntu 11.10 x64. I can log into a terminal and perform commands as usual, but I can't log in to the desktop. After I enter my username and password, some typical-looking start-up config info flashes on the screen, and then I get returned to the login screen. 

I've no idea what could have caused this as I rarely use this OS (I use Debian on sdb1). The only  recent action I've taken on the Ubuntu system was backing up 28G of stuff from Debian into an specially-created folder in the /home/user directory after mounting sda1 from inside Debian. The Ubuntu partition is now close to being full.

I've tried each of the following solutions in the order in which they appear here:

1. booting into different kernel versions

2. booting into recovery mode of various kernel versions(I just get the login screen again)

3. ```
sudo chown -R $USER:$USER $HOME
``` (no idea what this does; I just blindly used it)

4. deleting ~/.Xauthority

5. removing .profile (by renaming it; I restored it after confirming that the problem was unresolved)

6. checking ~/.xsession-error (it was empty)

7. trying to start up the desktop from the command line

8. uninstalling and re-installing my desktop (xfdesktop4)

At some late point in this trouble-shooting process, I began to get the message
```
iwlagn 0000:03:00.0: Aggregation not enabled for tid 0 because bad = 2
``` at the command line.
I've no idea what that means.

---

### Post by Bashing-om on 2015-06-27
StarKid; Hello; 

Look, release 11.10 long ago reached End_of_Life and no longer enjoys support.
Backup your data and install a current release . 14.04 is the current Long Term Support release. Supported 'til April 2019 !


[INDENT][INDENT]life then will be much better
[/INDENT][/INDENT]

---

### Post by Tk007LwZFJW5ej on 2015-06-27
I disagree. The reason that I backed up to the Ubuntu partition is because I'm trying to upgrade Debian (my external storage device has failed); Ubuntu is also my back-up OS in case I screw up the Debian upgrade. I rarely use Ubuntu (and it generally works fine when I do), I stopped using it because I was frustrated with the Ubuntu upgrade process, upgrading is a pain in and of itself, and I don't consider this problem to be so complex as to require any very specific 11.10 support, so there's not much of a reason to upgrade Ubuntu.

---

### Post by llamabr on 2015-06-27
> **StarKid said:**
> I don't consider this problem to be so complex as to require any very specific 11.10 support, so there's not much of a reason to upgrade Ubuntu.

There's actually lots of good reasons to upgrade, particularly if yours is so old.  Software has security problems, and others just stop being supported.

In any case, if your password is not working in the gui login, look at the bottom of the screen, and make sure it's using the right keyboard.  You might have accidentally changed it to swedish or hungarian, and then gnome is typing your password wrong (and since it's under the ***'s, you don't notice).

Let us know what happens.

---

### Post by Tk007LwZFJW5ej on 2015-06-27
> **llamabr said:**
> 
In any case, if your password is not working in the gui login, look at the bottom of the screen, and make sure it's using the right keyboard.  You might have accidentally changed it to swedish or hungarian, and then gnome is typing your password wrong (and since it's under the ***'s, you don't notice).

My password is working. I can log in via terminal.

---

### Post by llamabr on 2015-06-27
> **StarKid said:**
> My password is working. I can log in via terminal.

Right.  What I mean is that when you log in with the gui, if you look at the bottom, or side, or wherever (depending on your dm), you can change the keyboard language.  That's why it works fine via terminal, but on gui it doesn't (because on terminal, there's no gui to mess up your keyboard layout).

---

### Post by Tk007LwZFJW5ej on 2015-06-27
> **llamabr said:**
> Right.  What I mean is that when you log in with the gui, if you look at the bottom, or side, or wherever (depending on your dm), you can change the keyboard language.  That's why it works fine via terminal, but on gui it doesn't (because on terminal, there's no gui to mess up your keyboard layout).

When I enter an incorrect password, the log in interface gives me an error. I'm not getting that error.

---

### Post by cariboo on 2015-06-27
You mentioned that your Ubuntu partition is just about full, how much space do you have left? 

Your problem may also be due to a bad or corrupted video driver, the cure would be to re-install it, but you can't because 11.10 has reached EOL.

---

### Post by Tk007LwZFJW5ej on 2015-06-27
> **cariboo said:**
> You mentioned that your Ubuntu partition is just about full, how much space do you have left?

Ubuntu is on a 500G partition mounted at /mnt/ubuntu:

```
sudo du -chs /mnt/ubuntu/
452G    /mnt/ubuntu/
452G    total
```

To anyone: Maybe my permissions are messed up?

```
sudo ls -la /mnt/ubuntu/
``` gives:

total 152
drwxr-xr-x  27 root root  4096 Mar  6  2013 .
drwxr-xr-x   5 root root  4096 Apr  3  2014 ..
-rw-r--r--   1 root root     0 May 20  2012 0
drwxr-xr-x   2 root root  4096 Oct  4  2012 bin
drwxr-xr-x   3 root root 12288 Apr  2  2013 boot
drwxr-xr-x   2 root root  4096 Jan 16  2012 cdrom
drwxr-xr-x   5 root root  4096 May 20  2012 dev

etc. My username is nowhere to be found amongst the listings; they all only list root. Not sure if that's normal or not. And if not, would I just change the permissions directory by directory?

**Edit**: wait that doesn't make sense because I can access stuff by logging in at the terminal.

I'm going to try to create a new user and log in with that account.

---

### Post by Tk007LwZFJW5ej on 2015-06-27
Fixed. I simply deleted about 35G worth of data.

---

