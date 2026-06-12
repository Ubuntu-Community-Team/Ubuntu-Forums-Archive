---
title: "sudo won't let me enter password"
date: 2005-09-09
forum: General Help
---

### Post by Game master pro on 2005-09-09
Yeah the "sudo" thing in terminal doesn't work for me, well it works fine but lemme explin

i want to try making music play because yeah it doesn't play, so i read some posts and i think i got it, so i try going into terminal and typing

```

sudo gedit /etc/apt/sources.list

```

i got this from [here](http://www.ubuntuforums.org/showthread.php?t=46487).

So i type it and it asks for my password so i type it in and nothing happens, i type anything and it just won't show up on the screen, it doesn't let me type in my password, can someone tel me how to get this working, please?

---

### Post by lao_V on 2005-09-09
When you are typing the password it **won't** show it to you - not even asterisks! That is part of security feature. Just enter your own password and hit enter. Do you still get any errors?

---

### Post by tseliot on 2005-09-09
just type your password and press enter. No asterisks will be displayed. It's normal.

---

### Post by tseliot on 2005-09-09
We've answered together  :razz:

---

### Post by heimo on 2005-09-09
How about if you try another text editor?
 ```
sudo nano /etc/apt/sources.list
```

It's a bit harder to use, but still easy (this one runs in terminal). Type ctrl+X to exit (I'm not 100% sure) it should ask if you want to save.

EDIT: Oh, I completely misunderstood - I guess I'm too familiar with that behaviour. I thought you already entered password. Yeah, listen to the guys above.

---

### Post by codejunkie on 2005-09-09
[QUOTE=Game master pro]Yeah the "sudo" thing in terminal doesn't work for me, well it works fine but lemme explin

i want to try making music play because yeah it doesn't play, so i read some posts and i think i got it, so i try going into terminal and typing

```

sudo gedit /etc/apt/sources.list

```

i got this from [here](http://www.ubuntuforums.org/showthread.php?t=46487).

So i type it and it asks for my password so i type it in and nothing happens, i type anything and it just won't show up on the screen, it doesn't let me type in my password, can someone tel me how to get this working, please?[/QUOTE]

are you by chance using kde as your desktop enviorment?

---

### Post by Game master pro on 2005-09-09
Thanks guys for the quick reply  :) 

well, it started to work but then said this

"gmp is not in the sudeors file. This incedent will be reported"

Not sure what that means, but i did change my username, would that of caused it to not work?

codejunkie: Nope, i'm using gnome

---

### Post by codejunkie on 2005-09-09
[QUOTE=Game master pro]Thanks guys for the quick reply  :) 

well, it started to work but then said this

"gmp is not in the sudeors file. This incedent will be reported"

Not sure what that means, but i did change my username, would that of caused it to not work?

codejunkie: Nope, i'm using gnome[/QUOTE]
did you do a custom install if so your username might have not been stored in the sudoers file.

---

### Post by Game master pro on 2005-09-09
When i installed, i had my friend with me, and he's done it before, and he told me to do it in "expert" so yeah i typed expert, followed it all, and when i first installed i put my username as "nicholas" (which is my name) and after i installed it, i didn't like it so i went users and groups and renames my username to "gmp"

---

### Post by lao_V on 2005-09-09
You'll need to modify your sudoers file using the command visudo but I believe it will ask you for a password and since you are not in the sudoers file - it will not let you in. Basically you have locked yourself out as a superuser. I'm not even sure if you're gonna be able to change your username again to what it was before.

This issue was raised long time ago in this forum, maybe there is a solution somewhere.

---

### Post by heimo on 2005-09-09
Isn't there recovery mode or rescue mode or something like that in default Grub? (hit esc at the beginning of boot to choose), which doesn't ask root password? Or you could use Live CD, mount root partition and change sudoers file in /etc. No time to give exact instructions right now, but other people will help you (or you could search these forums, this is most probably at least in dozen threads).

---

### Post by Game master pro on 2005-09-09
Good thing i made a backup account just in case i did something stupid like that, ok so how exactly do i edit the sudoers file?

and yeah there is a "Ubuntu kernel (reovery mode)" option but that takes like 3 hours to work

---

### Post by lao_V on 2005-09-09
Yes the LiveCD, a great rescue tool!

---

### Post by codejunkie on 2005-09-09
[QUOTE=Game master pro]When i installed, i had my friend with me, and he's done it before, and he told me to do it in "expert" so yeah i typed expert, followed it all, and when i first installed i put my username as "nicholas" (which is my name) and after i installed it, i didn't like it so i went users and groups and renames my username to "gmp"[/QUOTE]
to add your name to the sudoers file reboot and at the grub menu choose recovery mode this will give you temp root access so you can enable the root account with ```
passwd root
```then reboot again with init 6 and follow this guide to add your name to the sudoers file
```
su
```
```
export EDITOR=gedit && visudo
```
add this at the end of file

yourusername	ALL=(ALL) ALL

---

### Post by Game master pro on 2005-09-10
What i don't exactly understand?

Reboot in recovery mode, and then what? where do i type "passwd root" am i spuuposed to boot it into terminal? and what's init 6? sorry i'm a noob, but i only installed ubuntu 3 days ago.

---

### Post by codejunkie on 2005-09-10
[QUOTE=Game master pro]What i don't exactly understand?

Reboot in recovery mode, and then what? where do i type "passwd root" am i spuuposed to boot it into terminal? and what's init 6? sorry i'm a noob, but i only installed ubuntu 3 days ago.[/QUOTE]
if you choose recovery mode at the grub menu it will take you into a terminal/like dos mode this gives you full root access to the system now just type 
```
passwd root
```and enter a new password this will enable the root/administrator account and ```
init 6
```is just a reboot command to restart the computer ```
reboot
``` might also work it does on some distros and some it doesn't if you have any problems let me know.

---

### Post by heimo on 2005-09-10
[QUOTE=Game master pro]What i don't exactly understand?

Reboot in recovery mode, and then what? where do i type "passwd root" am i spuuposed to boot it into terminal? and what's init 6? sorry i'm a noob, but i only installed ubuntu 3 days ago.[/QUOTE]


I've never used this Ubuntu recovery mode, but yes, it's terminal/console/command line/shell ... little blinking cursor on your screen in text mode. That's where you type those commands. *init 6* is just another way of telling your computer to reboot cleanly, probably command *reboot* will work fine too.


Follow the instructions above and you should be fine. If not, we'll be here waiting. :) Good luck. 


EDIT: Oh, codejunkie was awake too. :)

---

### Post by Game master pro on 2005-09-10
Ok thanks guys for your quick replys  :) 

I just did that and it's rebooting, it's now in normal ubuntu, or was i supposed to put it inti recovery mode again? 

[quote=codejunkie]
```

su

```

```

export EDITOR=gedit && visudo

```

add this at the end of file

yourusername ALL=(ALL) ALL
[/quote]

I'm kinda confused at this bit...

---

### Post by codejunkie on 2005-09-10
[QUOTE=Game master pro]Ok thanks guys for your quick replys  :) 

I just did that and it's rebooting, it's now in normal ubuntu, or was i supposed to put it inti recovery mode again? 



I'm kinda confused at this bit...[/QUOTE]
after you enabled the root account with "passwd root" reboot like you normally would and then run the other commands.

---

### Post by Game master pro on 2005-09-10
Do i log in as root and type them into terminal or something?

---

### Post by aveline on 2005-09-10
[QUOTE=Game master pro]Ok thanks guys for your quick replys  :) 

I just did that and it's rebooting, it's now in normal ubuntu, or was i supposed to put it inti recovery mode again? 



I'm kinda confused at this bit...[/QUOTE]
 why do some ppl insist on over complicating stuff... hehe

you have a login as another user yes? so login w/that user account.  Open a terminal, type ```
sudo visudo
``` it will then ask for your current accounts pword.

scroll down the page a lil & you'll see a line that says:

#user priviledge specification
root ....

change the line that says "root blah=blah" to "root ALL=(ALL) ALL".  Omit quotations.  When you're done editing hit CTRL-X to exit the thing & it should ask if you wanna save your work.

logout of that account & login w/the account you wish to use.

done.

aveline

---

### Post by codejunkie on 2005-09-10
[QUOTE=Game master pro]Do i log in as root and type them into terminal or something?[/QUOTE]
now that your in ubuntu open a terminal and type ```
su
```and enter the password you set it will show something like this 
```

root@ubuntu:/home/username#

```
when you get to this step copy and paste this code in the terminal 
```

export EDITOR=gedit && visudo

```
now add this line to the bottem of the file that opens
```

yourusername ALL=(ALL) ALL

```
click on file then save and exit that program and that should do it.

---

### Post by Game master pro on 2005-09-10
Thanks codejunkie that worked perfectly  :smile:

But another off topic question, when i boot into ubuntu it says

```

* Synchonizing clock to ntp.ubuntulinux.org...

```

But the problem is ubuntu is on another computer whihc doesn't have the internet, so it takes ages to try to do it, and in the end it just says

```

* Synchonizing clock to ntp.ubuntulinux.org...             [[COLOR=Red]fail[/COLOR]]

```

IS there any way to disable this, if theres not that's ok, i shall live  :)

---

### Post by codejunkie on 2005-09-10
[QUOTE=Game master pro]Thanks codejunkie that worked perfectly  :smile:

But another off topic question, when i boot into ubuntu it says

```

* Synchonizing clock to ntp.ubuntulinux.org...

```

But the problem is ubuntu is on another computer whihc doesn't have the internet, so it takes ages to try to do it, and in the end it just says

```

* Synchonizing clock to ntp.ubuntulinux.org...             [[COLOR=Red]fail[/COLOR]]

```

IS there any way to disable this, if theres not that's ok, i shall live  :)[/QUOTE]
i don't know of a way to disable it permently but when my network goes out i've noticed the same thing i just hit ctrl+c when it's loading to skip it hope that helps.

---

