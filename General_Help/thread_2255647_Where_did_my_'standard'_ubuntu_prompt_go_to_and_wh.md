---
title: "Where did my 'standard' ubuntu prompt go to and why ?"
date: 2014-12-06
forum: General Help
---

### Post by Nosphky on 2014-12-06
My bog-standard ubuntu terminal prompt, 'username@hostname ~$', has disappeared and suddenly become just a plain '$'.

This came about when I added a couple of lines at the end of my ~/.bashrc file to include a $HOME/bin entry in the PATH environmental variable.  The only change to .bashrc was adding these 2 lines :

PATH=$HOME/bin:$PATH
export PATH

( I had not appreciated that the   ~/.profile file would take care of including $HOME/bin into the $PATH environment variable for an interactive login shell.)

When I restarted, the PATH was as I wished but I had lost the original 'standard' prompt.  Reversing the changes to ~/.bashrc did not reverse this change to the prompt.   I know I can make further changes to .bashrc to customise the prompt but I wonder why what I did adding 2 lines caused the prompt to change.

So my question is which other file (files) were affected by my modification to ~/.bashrc ?

---

### Post by steeldriver on 2014-12-06
... I'd start by opening a terminal and running

```

diff ~/.bashrc /etc/skel/.bashrc

```

---

### Post by grahammechanical on 2014-12-06
The terminal is set up to open in our home folder. Which is named after our user name and it shows the name we have chosen for the installation. Which is another way of saying hostname.

Your terminal is now opening at the root folder. Type

code]ls[/code]

and you will see system files and folders including one for home.

When we edit system files a backup copy is also created automatically, It has the same name as the file we are editing but with the tilde character ( ~ ) as a prefix. This turns the backup into a hidden file. I have noticed that these backup files still get read by the system. And that could be the reason why your second editing of that file is not having an effect.

Regards.

---

### Post by Nosphky on 2014-12-06
@steeldriver :  diff ~/.bashrc  /etc/skel/.bashrc    gives :
 
91d90
< alias rm='rm -i'
116,118d114
< 
< # my main gpg key 
< export GPGKEY=asuj29fg

I dont know what 91d90 and 116,118d114 are but the alias and the gpg key were changes I made a few months ago.

@grahammechanical
pwd shows that I am in my home directory and 'ls' provides a full account of all the files in my home directory.  so I conclude that I am not in a root directory.

When I say that I reversed the mods made to .bashrc, in fact I did it by renaming .bashrc to something quite different and then renaming .bashrc~ to .bashrc.   And that's why the diff test suggested by steeldriver, above, does not show my two lines about the PATH change.

I have just discovered another (unwanted) effect.  When I use the up arrow key on the command line, it no longer gives previous commands but gives the following :  ^[[A and hitting enter gives :  "dash: 10: F: not found"

env gives -> SHELL=/bin/dash    .  It used to give /bin/bash .   So I must somehow have changed the shell.  I don't know how that happened.  Could that explain the other changes I see ?

---

### Post by matt_symes on 2014-12-06
Hi

If you type bash at the dash prompt, do you get a bash shell ?

If you get errors then post them back here.

kind regards

---

### Post by Nosphky on 2014-12-06
Matt :

If I type bash at the dash prompt, then the prompt goes back to the 'standard' prompt and I have a bash shell.  

env still gives SHELL=/bin/dash   - so somehow I've changed the login shell from bash to dash.

How do I change that back to bash ?

---

### Post by matt_symes on 2014-12-06
Hi

To change your shell, open a terminal and type

```
chsh -s /bin/bash $(whoami)
```

and reboot but look in /etc/passwd to see what that says is your login shell.

```
grep $(whoami) /etc/passwd
```

Look for /bin/sh or /bin/dash. If either of them are there then run the chsh command; if not them post back.

Kind regards

---

### Post by Nosphky on 2014-12-06
Thanks Matt -  I've now been able to change back to a bash login shell - confirmed in /etc/passwd

And prompts and cli history back to normal.   

So after all, it wasn't something I changed in ~/.bashrc but rather something else (I'm not sure what)  where I made an unintended change of my login shell from bash to dash.   A good learning experience.

---

### Post by mcduck on 2014-12-06
Also it's worh noting that you don't need to add ~/bin to your path, the default shell config files already do that for you automatically if you create the ~/bin directory. 

edit: I just read through the first post again and you ad already noticed the same thing, so ignore this. :D

---

