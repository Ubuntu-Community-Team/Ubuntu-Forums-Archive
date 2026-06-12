---
title: "problems with new kernel"
date: 2005-03-31
forum: General Help
---

### Post by sapo on 2005-03-31
Hi all  :mrgreen: 

I took 2 days to put the 3d support of my 9800pro working 100% on ubuntu 4.10 but now i ve update the system and its not working with the new kernel 2.6.10  :-( 

I have a 2.6.8 kernel that runs perfectly the 3d support if i boot with it  8) 

But i ve tried so many things before putting it to work that i dont remember what exactly i ve made.

I think i ve installed i kernel module or something like that... btw...

How can i put it to work with the new kernel?  [-o< 

The msg when i try fgl_glxgears is cant find fbconfig

Anyone knows what i have to do?  I dont want to take 2 days again trying a lot of things :( and instead i wanna learn how to put this * to work.

Thanx for any help

---

### Post by az on 2005-03-31
I have a weak graphics card, so I do not know first had, bu tin general to make a kernel module you need to install your kernel-headers (the package is called linux-headers.

You need the same version as the kernel you upgraded to.  Yes, you built a module for your other kernel, but since you made the module yourself, when you upgrade your kernel, the people who made your kernel have no idea about the extra modules you have.

SO, you have to built it again.

Once you have your headers, go to the directory where you unpacked the source for your module and build it.

There usually is a readme.

./configure
make
make install
(?)  Perhaps it is different, read the documentation from the driver source you got.

Also, I removed the bad word from your post.  Sorry.  I hate doing that, but no one really swears here.

---

### Post by Strider on 2005-03-31
sapo,
you need to compile the fglrx module specifically for the 2.6.10 kernel.  If you're using the kernel from the repository, you can download the fglrx module from the repository.  However, I recommend you compile the fglrx module as you will get better performance.

Here's a mini-howto I wrote a week or so ago to get the fglrx module compile and working.  You will need the kernel headers if you did not use a custom kernel:

[http://m6n.ath.cx/forum/viewtopic.php?t=382](http://m6n.ath.cx/forum/viewtopic.php?t=382)

Hope it helps.

-Mike

---

### Post by sapo on 2005-04-01
Thanx.. i ll try recompiling the module.... pray for me please   :roll:

---

### Post by sapo on 2005-04-01
a tried to recompile it but.. i dont have the headers.. and still i cant find the headers for the 2.6.10 kernel in the cdrom or apt-get.. so i will stay with my 2.6.8 kernel that is working fine :)

And another stupid bug... i removed the fglx driver and installed the ati fgl driver... and then my ut2k4 stopped working..

So i remembered that i had installed the MesaGL package... and reinstalled it... now its working fine.. take a look:

[[IMG]http://img217.exs.cx/img217/1170/screenshot29ja.th.png[/IMG]](http://img217.exs.cx/my.php?loc=img217&image=screenshot29ja.png)

The first error was with the ATI OpenGL library.. and then with the MesaGL it worked :mrgreen:

---

