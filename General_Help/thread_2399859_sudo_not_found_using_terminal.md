---
title: "sudo not found using terminal"
date: 2018-08-30
forum: General Help
---

### Post by seekertom on 2018-08-30
I have 16 and 18 both installed, 16 is the default, and is installed on hd partition 1. 
18 is installed on hd partition 2, which is labeled "1tbpart2". I enter 18.04 lts at grub menu during bootup.

Logged into 18, Im trying to install msw fonts from terminal. 
At term prompt: 

tom@tom-1tbpart2:~$ sudo su
sudo: command not found.

Now what?
Appreciate your help. st
:confused:

---

### Post by edadasiewicz on 2018-08-30
The sudo executable should have been installed in /usr/bin and /usr/bin should be in your PATH -- echo $PATH.

---

### Post by monkeybrain20122 on 2018-08-30
> **seekertom said:**
> 

tom@tom-1tbpart2:~$ sudo su
sudo: command not found.


Why would you want to sudo su to become root??!!

For your original question, try rebooting, Maybe the session was corrupt somehow, this happened to me a while back, rebooting fixed it.

---

### Post by seekertom on 2018-08-30
Yes, rebooting allowed me to use sudo.
Reason I used sudo su is because I have only teenie clue what I am doing. I understand $ prompt shows me I am currently using regular user permissions while # says I am root and have full admin permissions. hope this is correct. However, even so, I am not aware of how to tell which things require full admin. For example, I'm trying to install mscorefonts. seems like heavy duty stuff, so I opted to ask for full admin rights.

Unfortunately, I'm still getting my butt kicked. In this process, everything looks ok until web eula pops up with ok at the bottom. Ok isn't clickable or 'enter-able', and now term is hung up saying progress : [43%] and unchanging.

Guess this is off my orig topic, but maybe shows my frustration at not accomplishing my mission...
thanks, st

---

### Post by seekertom on 2018-08-30
Thanks for your input, but not helpful just knowing it should have been... needs to know, for example, if it needs reinstalling, how to do it... etc. in this case, other help suggested a reboot to fix, and luckily this time that worked. But I still sincerely appreciate your input. st

---

### Post by Bashing-om on 2018-08-30
seekertom; Hello -

Try this:
When the EULA pops up use the space bar to page down, Tab to highlight "Ok", then Enter.

sometimes the EULA is sneaky and is hidden behind other windows :(

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

