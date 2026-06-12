---
title: "Finding Folders"
date: 2008-02-06
forum: General Help
---

### Post by Commodore13 on 2008-02-06
I'm looking to find a folder on my desktop "intall_flash_player_9_linux"
but when I use the command cd install_flash_player_9_linux
it doesn't work
it says no such file or drive exists
also when I try to view documents or music folder it doesnt work either.
help?!?

---

### Post by stooshbunutu on 2008-02-07
use the file search from the places menu, that is the only way I have found that file/folder searching works.

Hope this helps :)

---

### Post by nemilar on 2008-02-07
If you're trying to do this through a terminal, and the files are on your desktop, you have to change directories to your desktop folder first:

```
cd ~/Desktop
```

---

### Post by geo909 on 2008-02-07
> **Commodore13 said:**
> I'm looking to find a folder on my desktop "intall_flash_player_9_linux"
but when I use the command cd install_flash_player_9_linux
it doesn't work
it says no such file or drive exists
also when I try to view documents or music folder it doesnt work either.
help?!?

Hi.
First of all. my answers below may be too obvious to you, I apologise if this is the case: When I started using linux, I couldn't even browse folders from the terminal so MAYBE this is the case for you. If not, then ignore my answer... 

So,

1)This "install_flash_player_9_linux"  file looks like an *installer*..
Are you sure that this is a folder and not a shell script or something?
Try 
>  sh install_flash_player_9_linux
or
> ./install_flash_player_9_linux

Maybe you will have to type those things with "sudo" in the beginning. Try it if they don't work (you will have to type your password, then).


2)If you followed the default options when you installed Ubuntu, then your computer was named something like *"(your username)-desktop*". That appears when you open a terminal, but you are NOT on "/home/(your username)/Desktop" folder. Maybe this is why the cd command doesn't work, I can't think of something else.
Open a terminal and try "*cd Desktop*" and then "*cd install_flash_player_9_linux*". 

 Sorry again if I mention things obvious to you

---

### Post by erfahren on 2008-02-07
> **Commodore13 said:**
> I'm looking to find a folder on my desktop "intall_flash_player_9_linux"
but when I use the command cd install_flash_player_9_linux
it doesn't work
it says no such file or drive exists
also when I try to view documents or music folder it doesnt work either.
help?!?
when opening a terminal session it opens by default to your /home/<username> directory (also refered to as merely "~/  " )

the Desktop is actually a subdirectory of your ~/ 

so to get tho that directory you mentioned it would actually be:
cd ~/Desktop/install_flash_player_9_linux

you can see the full path of the current directory you're in with "pwd" (print working directory)

> 
also when I try to view documents or music folder it doesnt work either.

I don't know, but maybe the above information will help you figure out what you're doing wrong

some more info on using the terminal
[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)
[https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html](https://help.ubuntu.com/ubuntu/desktopguide/C/linux-basics.html)
[Terminal for Beginners](http://ubuntuforums.org/showthread.php?t=73885)
[Know Your Terminal Commands, Terminal references](http://ubuntuforums.org/showthread.php?t=171507)

-- hope that helps

EDIT: I was a little slow when posting - oh well, I'll leave it. sorry to be redundant!

---

