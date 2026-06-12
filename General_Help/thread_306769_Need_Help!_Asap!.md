---
title: "Need Help! Asap!"
date: 2006-11-25
forum: General Help
---

### Post by Magiczero on 2006-11-25
hi 

I have an issue!!! I need to get it fixed ASAP! When I open Sanaptic I get this error: 

You have 2 broken packages on your system!

Use the "Broken" filter to locate them.

Then when I go to firefox everything is changed it says:

The proxy server is refusing connections i use no proxy. Oprea works fine.

Also when I go to update maniger I get this error:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

What's wrong here? How can i fix it?

As a resault I ran a tool that was going to fix it and I got this error

> tanner@tanner-desktop:~$  sudo apt-get install -f
Password:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
tanner@tanner-desktop:~$ 'dpkg --configure -a
> 










I need help because everything I am trying is not fixing it

Thanks

---

### Post by cantormath on 2006-11-25
did you try 
```
sudo dpkg --configure -a
```


another thing....
what are you trying to install?

you can also open synaptic and goto edit>fix broken packages....

---

