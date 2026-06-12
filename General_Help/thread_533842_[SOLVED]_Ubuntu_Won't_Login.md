---
title: "[SOLVED] Ubuntu Won't Login :|"
date: 2007-08-24
forum: General Help
---

### Post by guswashere on 2007-08-24
Well i've been running Ubuntu for about 3 days now, and recently when i installing JDK then logged into root, logged out,

now i can't login :[

it says

Your Session only lasted less than 10 seconds/ If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try loggin in with one of the failsafes to see if you can fix this problem

details:

/ect/gdm/PreSession/Default: Registering your session with wtmp and utmp
/ect/gdm/PreSession/Default: running: /usr/X11r6/bin/sessreg -a -w /var/run/utmp -x "/var/lib/gdm/ :0.Xservers" -h "" -l ":0" "gus"
/ect/gdm/Xsession: Beginning session setup...
/ect/profile: 17 :id: not found


Then it tries to run x- terminal-emulator and it fails..


I have 380 Gb of Diskspace so that isnt the problem.. same thing happens with i log in with root... and i try and login with the failsafes but it just get's all orange :(

thanks ahead for anyone that helps :KS

---

### Post by apetresc on 2007-08-24
Hi :) This problem should be easily fixable. The problem is not with logging into Linux, just with logging into GDM. Do this:

At the GDM prompt (where you usually login), instead of logging in, press Ctrl+Alt+F2. This will take you to a text-only terminal. Log in as your user. Once you're in, type: ```
rm ~/.ICEauthority
``` Then reboot and try logging in again through GDM; it should work this time.

Good luck :)

---

### Post by guswashere on 2007-08-24
thanks, I tried that but... 

It says i don't have Rm installed,

I tried apt-getting that,

then it said

The program 'apt-get' is currently not installed. You can install it by typing apt-get install apt

:confused::confused::confused:

lol can anyone else help out?

---

### Post by apetresc on 2007-08-24
Oooh boy. If "rm" and "apt-get" aren't found, there's a very serious problem here. Most likely you messed up your path when installing the JDK.

What is the output of the ```
echo $PATH
``` command?

---

### Post by guswashere on 2007-08-24
it says $PATH:/usr/local/jdk/bin


yea.. i think i screwed it up pretty bad :oops:

---

### Post by apetresc on 2007-08-24
> **guswashere said:**
> it says $PATH:/usr/local/jdk/bin


yea.. i think i screwed it up pretty bad :oops:

Yup, there's your problem :) Don't worry, this is definitely fixable. What is the contents of your .bash_profile and .bashrc files in your home directory? (If you don't have one of these files, just paste the contents of the one you do have)

---

### Post by guswashere on 2007-08-24
Um.... How do i find that out?

---

### Post by apetresc on 2007-08-24
> **guswashere said:**
> Um.... How do i find that out?
Using the 'cat' utility. Log in to the terminal like you did before, then type:
```
cat ~/.bash_profile
cat ~/.bashrc
```
I'm specifically looking for any lines with "PATH=" in them.

---

### Post by guswashere on 2007-08-24
The program 'cat' is currently not installed -_- then same thing that Rm does..
And when i try and log in throught the gnome failsafe it just ends up being and orange screen :frown:

---

### Post by apetresc on 2007-08-24
> **guswashere said:**
> The program 'cat' is currently not installed -_- then same thing that Rm does..
And when i try and log in throught the gnome failsafe it just ends up being and orange screen :frown:
Oooh, right, I forgot, you have no path so of course cat won't work :) No worries. Before you type the cat commands, simply type this first: PATH=/bin:$PATH
Then type the cat commands I showed you above, they should work now. Tell me about any lines in those files that have "PATH=" in them.

---

### Post by guswashere on 2007-08-24
Well the first one doesnt work, but the second one works, but there is no PATH= in there :|

A guide I read on changin the variables for Java said to change it in /ect/enviroment
Then It told me to add some things, which I did in there, would that be the cause of the problem? If so how would I be able to change it so that I can revert it because I know what to delete..

---

### Post by apetresc on 2007-08-24
> **guswashere said:**
> Well the first one doesnt work, but the second one works, but there is no PATH= in there :|

A guide I read on changin the variables for Java said to change it in /ect/enviroment
Then It told me to add some things, which I did in there, would that be the cause of the problem? If so how would I be able to change it so that I can revert it because I know what to delete..
Ah, okay, so it was in /etc/environment that you made your change! Good. Now all you have to do is this:
Type PATH=$PATH:/usr/bin
This adds /usr/bin to your path, which you will need to run nano or vim.
Then type: vim /etc/environment (or nano /etc/environment, whichever text editor you know how to use)
Once you're in that file, find the line that says PATH=/usr/local/jdk/bin or something along those lines. Delete that line. (If you're using vim, just type "dd" and it will get deleted.
Then reboot your computer and you should be all set. Let me know how it goes.

---

### Post by guswashere on 2007-08-24
Ok.. I tried accessing it with both Text Editors but apparently the file doesnt exist -_-

now what? :confused:

---

### Post by guswashere on 2007-08-24
bump?

---

### Post by guswashere on 2007-08-24
help >_<

---

### Post by apetresc on 2007-08-24
> **guswashere said:**
> Ok.. I tried accessing it with both Text Editors but apparently the file doesnt exist -_-

now what? :confused:

Are you sure you typed it right? You said earlier that you modified this file to add the JDK to the path. How did you edit if it doesn't exist...?

Clearly there is some file in your shell's startup that is getting sourced and which resets your path. If it's not .bash_profile or .bashrc it has to be something in /etc ...

EDIT: And sorry for the long response time, I had to go to a meeting. I'm at work ;)

---

### Post by guswashere on 2007-08-24
well i retyped it in hopin it would work makin sure that i typed it in correctly..

And yet to no avail it did not work :|

what should I do?

EDIT 

I typed in ect instead of Etc :P

Sorry for the trouble lol..


Thanks for all the help tho =]

---

### Post by apetresc on 2007-08-24
> **guswashere said:**
> 
I typed in ect instead of Etc :P

Sorry for the trouble lol..


Thanks for all the help tho =]

Haha ;) Well, since you marked the thread solved, I'm guessing you removed the line. This fixes your login problem but probably breaks your JDK. 

What you probably did was add ```
PATH=/usr/local/jdk/bin
``` when you SHOULD have written ```
PATH=$PATH:/usr/local/jdk/bin
``` The first command REPLACES the path with /usr/local/jdk/bin. The second command ADDS it to the path. You want the second one. It should be safe now to edit your /etc/environment file with the SECOND line, and your jdk will work :)

Or you can just use ```
sudo apt-get install sun-java6-jdk
``` which is much easier ;) Just make sure you have the multiverse repository enabled.

---

