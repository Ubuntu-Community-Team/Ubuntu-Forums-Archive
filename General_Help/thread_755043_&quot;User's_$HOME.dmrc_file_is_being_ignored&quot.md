---
title: "&quot;User's $HOME/.dmrc file is being ignored&quot; ...help."
date: 2008-04-14
forum: General Help
---

### Post by plvral on 2008-04-14
Hi ...I'm at the end of my rope trying to figure this out, so any help would be greatly appreciated!

I'm completely new to Ubuntu (and Linux) - having installed it two days ago, but have really enjoyed it thus far up until this point.

Basically, the problem I encountered occurred when I renamed my login username (through the administration menu) and thought why not also change the name of the home directory so it would match. Big mistake. After rebooting I received this message, "User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other use"

I searched for the solution in the forums and elsewhere, coming across suggestions/solutions and tried them to no avail. I recognize that the problem is essentially based on this .dmrc file and accessibility/permissions - but I don't know how to change this in a step by step manner. The forums provided me with some info, but I keep running into dead ends.

I made a new user (two actually) with the hopes of them having administration powers, but that backfired.

For more info, here is the output of ls -la /home


plvral@Ubuntu:~$
drwxr-xr-x  5 root   root   4096 2008-04-14 08:40 .
drwxr-xr-x 22 root   root   4096 2008-04-13 02:51 ..
drwx------ 78 me     me     4096 2008-04-14 05:26 me
drwxr-xr-x 18 plvral plvral 4096 2008-04-14 11:08 plvral
drwxr-xr-x 19 rjb    rjb    4096 2008-04-14 11:07 rjb
 
"me" is the original username that I wish to regain access for, a place I cannot get to at all; where the home directory with important files reside. "plvral" and "rjb" are the subsequent usernames I made to try and fix the problem of "HOME/.dmrc file is being ignored"

I tried:

sudo chown -R [username] /home/[username]
sudo chmod -R 755 /home/[username]
sudo chown [username] $HOME/.dmrc
sudo chmod 644 $HOME/.dmrc

but the result read:

plvral@Ubuntu:~$ sudo chown -R me /home/me
[sudo] password for plvral:
plvral@Ubuntu:~$ sudo -R 755 /home/me
sudo: illegal option `-R'
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
plvral@Ubuntu:~$


trying it again I get:

plvral@Ubuntu:~$ sudo chown -R me/home/me
plvral@Ubuntu:~$ sudo chmod -R 755 /home/me
plvral@Ubuntu:~$ sudo chown me $HOME/.dmrc
plvral is not in the sudoers file.  This incident will be reported.

So I don't know if I have to delete those other usernames, but creating a new user did allow me to at least login and write make this post  : )

I'm sure there are folks around who can help, but it might be an issue of them reading this post. Fingers crossed!

---

### Post by pytheas22 on 2008-04-14
The chmod and chown commands should solve the problem.  However your first couple attempts involved typos, and when the commands finally ran successfully, it looks like plvral may not have had administrator privileges.

Log in to the command-line under the user "me"--since this was the first account on the system, it should have sudo permission--and then run:

```
sudo chown -R me/home/me
sudo chmod -R 755 /home/me
sudo chown me $HOME/.dmrc
```

Does this work?

---

### Post by plvral on 2008-04-14
thanks for the reply.. but sadly it didn't work.

when trying to log in with the "me" username, i can only sign into the "failsafe terminal" - it's the only session type which allows me anything.

so i tried your suggestion above and after the first line i get:

chown: missing operand after 'me/home/me'

and I don't know if I made matters worse, but after my first post I tried to change the home directory name, thinking that would help ...the new home directory of "me" is 'home/me_home'

aghhh....

---

### Post by pytheas22 on 2008-04-14
Sorry, it didn't work because there was a typo that I had copied-and-pasted.  I would move me_home back to just me.  Try this, under the account "me":

```

sudo mv /home/me_home /home/me
sudo chown -R me /home/me
sudo chmod -R 755 /home/me
sudo chown me $HOME/.dmrc
```

---

### Post by plvral on 2008-04-14
how do i change 'me_home' back to 'me'? (changing it in the first place was a result of not knowing what i was doing).

---

### Post by pytheas22 on 2008-04-14
You can change it with the command

```
sudo mv /home/me_home /home/me
```

---

### Post by cdenley on 2008-04-14
What do you mean change it? Change the user configuration, or change the directory itself?

If you want to change a user's home path, use this command
```

sudo usermod -d /path/to/home username

```

If you want to rename a directory
```

sudo mv /path/to/old_dir /path/to/new_dir

```

If you want to change ownership recursively (this shouldn't change if the uid doesn't)
```

sudo chown -R user /path/to/dir

```

---

### Post by Gen2ly on 2008-04-14
learn something new everyday.

good stuff cdenley.

---

### Post by plvral on 2008-04-14
it still didn't work.. triple checking there were no typos, i was told:

chown: cannot access '//.drmc': No such file or directory

after typing what you said:

sudo chown -R me /home/me
sudo chmod -R 755 /home/me
sudo chown me $HOME/.dmrc

is there a space between $HOME/ .dmrc?
should I try something other than "$HOME"?

do you think it would make a difference if i delete the other two newly created users? perhaps setting "me" without any permissions competition?

i cannot even access anything in my "home" folder ..otherwise i would get the needed files and reinstall ubuntu.

sorry for being a headache.. but this is making me crazy. so much for user friendly linux!

---

### Post by pytheas22 on 2008-04-14
Try running:

```
sudo chown me /home/me/.dmrc
sudo chmod -R 755 /home/me
sudo chmod -R 755 /home/me/.dmrc

```

You could also access the files in /me/home by logging in with one of the accounts that works, opening a terminal and typing "sudo nautilus"  Then you should be able to navigate to /me/home and copy the files you want out.  Reinstallation might be the simplest solution if the command above doesn't work; it's not clear why you're getting this error anyway, but it looks like something might be screwed up.

---

### Post by plvral on 2008-04-14
after trying "sudo usermod -d /path/to/home username" ...i'm alerted that "Your home directory is listed as: '/path/to/home' but it does not appear to exist. Do you want to log in with the /(root) directory? It is unlikely anything will work unless you use a failsafe session"

Which is when I use the failsafe terminal ...where I've been trying these various commands.

This all started by changing the first username "me" to "plvral" and then changing the "home/me" to "home/plvral"  ...and now I have to reinstall the entire ubuntu operating system? really?

---

### Post by pytheas22 on 2008-04-14
> This all started by changing the first username "me" to "plvral" and then changing the "home/me" to "home/plvral" ...and now I have to reinstall the entire ubuntu operating system? really?

Do you mean that you just renamed the folder /home/me to /home/plvral?  That would explain what happened.

Also, run this command:

```
sudo usermod -d /home/me me
```

/path/to/home and username needed to be replaced with the right values:)

---

### Post by cdenley on 2008-04-14
I didn't mean to use that command literally. Pay attention to the words in those commands.
```

sudo usermod -d /path/to/home username

```
Replace "/path/to/home" with whatever path you want the user's home to be. You can make it whatever path you want. If the path doesn't exist, or that user doesn't have permission to read/write to it, then you will have problems. Change username the user's name for which you are changing the home directory's path. For example my command would be
```

sudo usermod -d /home/cdenley cdenley

```

---

### Post by bodhi.zazen on 2008-04-14
~/.dmrc needs permissions of 644

I am not following your user name and home directory. Usually your home directory is /home/user_name

Go ahead an boot to recovery mode and try this : 

.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
sudo chown user_name .dmrc
sudo chmod 755 /home/user_name
sudo chown -R user_name /home/user_name


where user_name = your log in name.

OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
sudo chmod 755 /home/user_name
sudo rm -rf /home/user_name/.dmrc

Where  user_name = your log-in name :p

If that fails, what did you do ? Move home ?

---

### Post by plvral on 2008-04-14
goodness, it finally worked!

first i did:

sudo usermod -d /home/me me

then in recovery mode:

sudo chown -R user_name /home/user_name
sudo chmod 755 /home/user_name
sudo rm -rf /home/user_name/.dmrc 

and this one worked (the first suggestion didn't seem to)

so thanks for everyone's help! really, reapply appreciated ... and before this thread is killed - can i delete the two new users 'plvral' and 'rjb' which were created as test-dummys ...those can be created without any harm or side effects?  i figured i should ask just in case...

what a busy 'day three' on ubuntu!

---

### Post by chrisby on 2008-05-03
I had this same problem and fixed it with:

1.in terminal:  Sudo nautilus

2. browse to /home

3. right click-> properties

4. Under permissions make sure owner can create and delete, group can access, and others can access.

5. click apply permissions to enclosed files

6. enjoy!

---

### Post by Longun on 2008-05-14
> **pytheas22 said:**
> Sorry, it didn't work because there was a typo that I had copied-and-pasted.  I would move me_home back to just me.  Try this, under the account "me":

```

sudo mv /home/me_home /home/me
sudo chown -R me /home/me
sudo chmod -R 755 /home/me
sudo chown me $HOME/.dmrc
```


Just for info this worked for me.  I didn't change anything I just suddenly got this error after backing up my home directory.

Thanks

---

### Post by AlbertTatlocksCap on 2008-05-16
Ok - i have had this same problem before after my Gutsy upgrade and solved it ...


This has now happened again on 8.04 following the software updates in the last couple of days 

It happened both on my laptop and desktop machine (both desktop version)
The desktop was a fresh install
The laptop was a beta followed by the updates

I saw it first on the laptop, then did software updates on the desktop and after a reboot, the error was there

I will correct it - but it may be useful information for you

---

