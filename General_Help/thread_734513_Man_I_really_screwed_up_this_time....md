---
title: "Man I really screwed up this time..."
date: 2008-03-24
forum: General Help
---

### Post by starfox5194 on 2008-03-24
ok so this is like my fourth day using ubuntu... and i already F***** it up!

I got everything working fine until i try and compile wine on my system.

i had to add libraries to get the thing to compile correctly. when i selected the items to install, there was a list of things that synaptic wanted to uninstall.

They looked like they shouldn't be uninstalled. some of them were ubuntu-desktop. and some nvidia drivers. I thought that might've been normal to happen, but i guess not.

So now my current status is that linux boots in low res mode. and when i use envy the install crashes.

can somebody tell me what files i may need to install to get my system back yo normal.

Things i've tried already. 

Using synaptic to reinstall ubuntu-desktop. worked correctly.
going into base system files and clicking random files in hope of correcting this error.

I am sorry if this is hard to understand my head is all jumbled up at the moment.
If you need any more information, I can give it to you. I am pretty good at figuring things out. and know a bit of linux by now.

Specs

Q6600 @ 2.4
4 GB Ram
Geforce 8800 GTS 512
Ubuntu 7.10 Gutsy Gibbon AMD 64 Edition
Bad Axe 2 Mobo

If there is any way to fix this error without me having to redo my desktop theme and re-obtain all of my applications that i currently have it would be greatly appreciated.

Thanks a lot in advanced.

---

### Post by skyjacker on 2008-03-24
I can't tell you what file(s) you need to fix your problem, but when you get it corrected you should always check the repositories to see if the application you want to install is in there. (Wine is, and it is a no-hassle install. That way you shouldn't have to mess with dependencies,etc.  You may end up doing a complete re-install.  Good Luck.

---

### Post by meg23 on 2008-03-24
Nintendol337, prepare to be banned from ubuntu forums. DO NOT ENTER THAT COMMAND!

I am not sure if you tried this, but search synaptic for nvidia and find nvidia-glx-new. That is probably the driver you need. Make sure it is installed. If it is installed, reinstall it. Also check to make sure nvidia-kernel-common is also installed and if necessary reinstall it. I had a similiar issue and it fixed the problem.

---

### Post by starfox5194 on 2008-03-24
ok

i just saw your replies and fortunately came to a conclusion that rm -rf was NOT the way to go.

I tried your fixes and sadly they had no effect at all.

 i was trying to compile wine because i wanted a certain version that would support my exact os.
 any other ideas

---

### Post by kool_kat_os on 2008-03-24
> **meg23 said:**
> Nintendol337, prepare to be banned from ubuntu forums. DO NOT ENTER THAT COMMAND!

I am not sure if you tried this, but search synaptic for nvidia and find nvidia-glx-new. That is probably the driver you need. Make sure it is installed. If it is installed, reinstall it. Also check to make sure nvidia-kernel-common is also installed and if necessary reinstall it. I had a similiar issue and it fixed the problem.

why would he/she be banned for 'using' the command?

---

### Post by meg23 on 2008-03-24
well, there was big message on the board a few months ago that anyway who advises someone to use a malicious script would have their IP address blocked from the website. Its not a good idea to even joke with these codes, eventhough, both you and I know it will completely delete someones filesystem. Someone might not know, and it could really ruin someones day. 

[http://ubuntuforums.org/announcement.php?a=54](http://ubuntuforums.org/announcement.php?a=54)

---

### Post by starfox5194 on 2008-03-24
ok well here is the output of when envy fails to run my install... 

it worked when i first installed ubuntu

screenshot
[[IMG]http://img186.imageshack.us/img186/9603/screenshotvg8.th.png[/IMG]](http://img186.imageshack.us/my.php?image=screenshotvg8.png)

And yes i did try to do what meg23 suggested in synaptic with no luck... =[

---

### Post by Tyke91 on 2008-03-24
it sounds painful, and I wound up doing this the first week I had ubuntu, but you should probably just do a clean re-install and start over again. this time, check to see if something is in the repositories before you go messing with file dependencies :)

don't worry, everybody does it.


PS: I second that you should NEVER run any sort of terminal command that you aren't certain about. please, if someone ever suggests that you type a command, google it first to make sure :)


you've had a bumpy ride, but welcome to ubuntu... I hope that we can help you

---

### Post by starfox5194 on 2008-03-25
ok...

i guess i am going to do a clean reinstall...

Is there a way for me to save my Wine, Cedega, and virtualbox installations?

all i really need is the things i put into the programs. not the actual games.

Ex Windows XP Halo combat evolved Battlefield 2142.

in many of the windows os there is a system restore option that kept a complete backup of your system if something like this were to happen. Does anyone know of a clone of this for linux?

thanks a lot for your help

---

### Post by sailor2001 on 2008-03-25
remastersys   in synaptics

---

