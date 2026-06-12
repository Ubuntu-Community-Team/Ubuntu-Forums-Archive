---
title: "PATH$ error"
date: 2013-02-02
forum: General Help
---

### Post by RocketPenguin on 2013-02-02
Welcome to all! I haven't been on ubuntuforums for a while, meaning i haven't had any problems, but alas! I have yet another problem and need your peaoples help. I was installing something using terminal, and the PATH$ said that i need to choose the location of the path. I did so, and the command worked fine. The problem is, every time i enter a command involving path, i get the error

 > The command could not be located because '/usr/bin (in this case, any location)' is not included in the PATH environment variable.

How do i fix this??? How do i get the PATH$ back to what it's suppose to be?Thanks for your time and help,
Linux Junkie

---

### Post by Lars Noodén on 2013-02-02
If you close the terminal and open it again, the $PATH should be reset to what is set in ~/.profile or /etc/environment.  That is, if you did not change it in ~/.bashrc or ~/.profile.   Where did you change it?

---

### Post by sudodus on 2013-02-02
What is your path now? [COLOR="Red"]Please post the output of the following command[/COLOR]
```
echo $PATH
```

I'm running Ubuntu 12.04 and I have the following path

```
/home/sudodus/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/games
```

- There is a duplicate for games (that should be removed).
- The first item was automatically added, when I made a ~/bin directory for my own executables.
- The second item was automatically added because of the X display manager used in my system (lightdm).

- I think the rest of the items come from the file [FONT="Courier New"][SIZE="3"]/etc/environment[/SIZE][/FONT]

which contains one line for PATH and one line for LANG

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="sv_SE.UTF-8"
```

So I suggest that you make a backup copy of that file

```
sudo cp /etc/environment /etc/environment.old
```
and then edit the file to include what should be there (for example copy the content of my PATH=... line, but keep your language entry)
```
sudo nano /etc/environment
```

Use nano or the editor you like the best, but remember to run it with superuser privileges.

Reboot and see if it helps. If no luck, there is something that overwrites your path, and you need to find it, or overwrite it again, which might be tricky.

---

### Post by RocketPenguin on 2013-02-02
> **sudodus said:**
> What is your path now? [COLOR="Red"]Please post the output of the following command[/COLOR]
```
echo $PATH
```

I'm running Ubuntu 12.04 and I have the following path

```
/home/sudodus/bin:/usr/lib/lightdm/lightdm:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/games
```

- There is a duplicate for games (that should be removed).
- The first item was automatically added, when I made a ~/bin directory for my own executables.
- The second item was automatically added because of the X display manager used in my system (lightdm).

- I think the rest of the items come from the file [FONT="Courier New"][SIZE="3"]/etc/environment[/SIZE][/FONT]

which contains one line for PATH and one line for LANG

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="sv_SE.UTF-8"
```

So I suggest that you make a backup copy of that file

```
sudo cp /etc/environment /etc/environment.old
```
and then edit the file to include what should be there (for example copy the content of my PATH=... line, but keep your language entry)
```
sudo nano /etc/environment
```

Use nano or the editor you like the best, but remember to run it with superuser privileges.

Reboot and see if it helps. If no luck, there is something that overwrites your path, and you need to find it, or overwrite it again, which might be tricky.


Mk, so the output is: > $/Home/Dev/:/home/jeremiah/Dev/android-sdk-linux/tools:/home/jeremiah/Dev/android-sdk-linux/platform-tools
I think thats the problem... And about your other commands, every time i do a sudo command i get the same error: Command > 'sudo' is available in '/usr/bin/sudo'
So i guess i permanently changed the PATH$, screwing it up...
EDIT: The reason it says android is because i was trying to install an android emulator, and one command told me to put in my path file, which may have screwed it up.

---

### Post by RocketPenguin on 2013-02-02
Not sure where, but i think i permanently changed the path.

---

### Post by sudodus on 2013-02-03
Try to repair it booted from a live system: Boot from your Ubuntu install CD/USB drive.

Run ```
sudo fdisk -lu
``` and ```
sudo blkid
``` to identify your partitions.

Mount the root partition of the installed ubuntu system, probably /dev/sda1, /dev/sda5 or /dev/sda6. Use the file browser to mount/umount. Let's say your system is mounted on /media/ubuntu (the name may vary depending of if you use labels).

 ```
sudo cp /media/ubuntu/etc/environment /media/ubuntu/etc/environment.old
```
and edit the file with
```
sudo nano /media/ubuntu/etc/environment
```

But if that file is good, and your path is still bad, it is changed somewhere. Check also the locations suggested by Lars Noodén, where ***~*** should translate to something like ```
/media/ubuntu/home/jeremiah
``` when running the live system.

You might also try to search for PATH= in the /etc directory

```
sudo grep -r "PATH=" /media/ubuntu/etc/*
```
and for android-sdk-linux
```
sudo grep -r "android-sdk-linux" /media/ubuntu/etc/*
```
which might help you find where your path is reset.

---

### Post by RocketPenguin on 2013-02-03
So, basically reset my PATH$? I have used commands before, but never got too far into it, and sadly your help doesn't make too much sense, lol... But i could look up like a tutorial and follow that, right? Or make your commands a wee bit easier to understand for me? The partition is /dev/sda2 i don't think it has a name other than that... And my username is jeremiah . So, could you make your commands fit these specifications? It would be great...

---

### Post by sudodus on 2013-02-04
> **linux junkie said:**
> So, basically reset my PATH$? I have used commands before, but never got too far into it, and sadly your help doesn't make too much sense, lol... But i could look up like a tutorial and follow that, right? Or make your commands a wee bit easier to understand for me? The partition is /dev/sda2 i don't think it has a name other than that... And my username is jeremiah . So, could you make your commands fit these specifications? It would be great...

0. Boot from the install CD/USB drive

1. Use the file browser to mount /dev/sda2 (click on its icon in the left panel)

2. Run the command```
df
``` and post the output.

Then I will try to give detailed instructions :-)

---

### Post by Vaphell on 2013-02-04
somehow you have overwritten the $PATH variable entirely instead of merely appending your own directories to the default value
it should be
```
PATH=**$PATH**:/some/dir1:/some/dir2
```
not
```
PATH=/some/dir1:/some/dir2
```

---

### Post by rnerwein on 2013-02-04
> **linux junkie said:**
> Welcome to all! I haven't been on ubuntuforums for a while, meaning i haven't had any problems, but alas! I have yet another problem and need your peaoples help. I was installing something using terminal, and the PATH$ said that i need to choose the location of the path. I did so, and the command worked fine. The problem is, every time i enter a command involving path, i get the error

 

How do i fix this??? How do i get the PATH$ back to what it's suppose to be?Thanks for your time and help,
Linux Junkie
hi
i must tell you: this error message i have never seen !!!! (sytem will tell you "command not found - or ???).

just a hint: it's not PATH$ it is $PATH and if you want to expand your orginal PATH (take the last line in your ~/.bashrc) you have to do it in the following way:
PATH=$PATH:/your_new_paths seperated by ":"
export PATH
by the side: i know you can write: export PATH=bla blabla
but the original "sh" will give you an error if you write it on the same line
cheers

---

### Post by dan000 on 2013-02-04
> **Lars Noodén said:**
> If you close the terminal and open it again, the $PATH should be reset to what is set in ~/.profile or /etc/environment.  That is, if you did not change it in ~/.bashrc or ~/.profile.   Where did you change it?

I think this is the answer. Have you checked ~/.bashrc and ~/.profile for any lines that set $PATH? They would start with PATH=... or export PATH=...

Please do this before you go to the trouble of rebooting into a live CD and doing a lot more complicated stuff (Occam's Razor here, people).

---

### Post by RocketPenguin on 2013-02-04
So, do i just enter ~/.bashrc and ~/.profile? The result was: bash: /home/jeremiah/.bashrc: Permission denied

---

### Post by dan000 on 2013-02-04
> **linux junkie said:**
> So, do i just enter ~/.bashrc and ~/.profile? The result was: bash: /home/jeremiah/.bashrc: Permission denied
No, you need to edit those files. If you're stuck in a command-line, try using nano, so
```
nano ~/.bashrc
```
Look for a line that changes PATH, and delete it (or at least, fix it).

---

### Post by RocketPenguin on 2013-02-05
> Command 'nano' is available in the following places
 * /bin/nano
 * /usr/bin/nano
The command could not be located because '/usr/bin:/bin' is not included in the PATH environment variable.
nano: command not found This was the output.

---

### Post by dan000 on 2013-02-05
Well, of course, since you screwed up your $PATH. You'll have to specify the entire path to nano, so 
```
/usr/bin/nano ~/.bashrc
```

---

### Post by RocketPenguin on 2013-02-05
Now what??? 
> # ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

# If not running interactively, don't do anything
[ -z "$PS1" ] && return

# don't put duplicate lines or lines starting with space in the history.
# See bash(1) for more options
HISTCONTROL=ignoreboth

# append to the history file, don't overwrite it
shopt -s histappend

# for setting history length see HISTSIZE and HISTFILESIZE in bash(1)
HISTSIZE=1000
HISTFILESIZE=2000

# check the window size after each command and, if necessary,
                               [ Read 105 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Text^T To Spell

---

### Post by dan000 on 2013-02-05
It's a text editor. Find the lines that mention PATH (read my previous comments), and get rid of them. Use the arrow keys to move around the document, and Backspace to delete.

Seriously, how hard is it to use a text editor? If you need this much hand-holding to edit a text file, you should probably just reinstall from scratch, and stay completely away from the command line, and not install anything outside of Ubuntu's official repos, until you've learned a lot more.

---

### Post by RocketPenguin on 2013-02-06
Thanks man, thanks. Real kind of you. Anyway, i deleted the lines that contained $PATH, so now what? Should all be well? The reason of this forum is for people who don't know how to fix the problem, and need help. As i understand, hand holding isn't a bad thing, thats what this forum is for.
Thanks again, :)

---

### Post by Impavidus on 2013-02-06
Let's hope it solved your problem. If the problem is was not in your .bashrc you may have to check .profile. In my case it contains the following PATH related lines:```

# set PATH so it includes user's private bin if it exists
if [ -d "$HOME/bin" ] ; then
    PATH="$HOME/bin:$PATH"
fi
```
which just adds ~/bin to the PATH.

Else take a look at /etc/profile and /etc/bash.bashrc (no references to PATH in mine) and finally at /etc/environment, containing the default PATH:```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
```Other files that can influence the PATH aren't present by default (although they can be added).

---

### Post by RocketPenguin on 2013-02-06
Thank you!! That got it, and all works now.
Thanks again for all those who helped!!!

---

