---
title: "Severe Ubuntu Desktop Issue [16.04]"
date: 2017-03-11
forum: General Help
---

### Post by zobar on 2017-03-11
I've set up a dedicated server with OVH hosting, and I've been trying to install LXDE for the past few hours, without success.

At this point, I have done a clean reinstall perhaps 10 times before turning for support here.

For the last set up I did, I immediately updated the machine, and did apt-get install ubuntu desktop. Afterwards, I did apt-get install lxde. Both of these worked without error. I then rebooted the machine, which took place without errors.

I then ran the startx command, and my machine froze and then died.

What could be the issue? I've tried this about 10 different ways before turning here, though I can't remember the previous methods I attempted.

---

### Post by HermanAB on 2017-03-11
A dedicated server - running remotely in a data centre - and you want to run a desktop on it?

That won't work, because the machine doesn't have a screen, keyboard or mouse attached to it - it is 'headless' - so X won't run on it.

However, since you have installed the graphical desktop utilities and programs, you can run them remotely and let them render on your local desktop using ssh, provided that your local desktop runs X.

So, assuming that your local desktop is Linux (or Windows with Cygwin), simply do something like this:
$ ssh -X user@serveripaddress nameofprogram

and that program will then transparently pop up on your local desktop.

or another example:
$ ssh -X herman@1.2.3.4 "gedit testfile.txt"

---

### Post by zobar on 2017-03-11
> **HermanAB said:**
> A dedicated server - running remotely in a data centre - and you want to run a desktop on it?

That won't work, because the machine doesn't have a screen, keyboard or mouse attached to it - it is 'headless' - so X won't run on it.

However, since you have installed the graphical desktop utilities and programs, you can run them remotely and let them render on your local desktop using ssh, provided that your local desktop runs X.

So, assuming that your local desktop is Linux (or Windows with Cygwin), simply do something like this:
$ ssh -X user@serveripaddress nameofprogram

and that program will then transparently pop up on your local desktop.

or another example:
$ ssh -X herman@1.2.3.4 "gedit testfile.txt"

Thank you for your response! :P

It all makes sense now.

There is still a small issue that I am experiencing. When I do ssh -X  root@149.202.87.89 lxde, it doesn't run the lxde environment on my local screen. Instead, it says "command not found." Why would this be?

---

### Post by HermanAB on 2017-03-11
Because lxde is not a single program.  Lxde is a desktop *environment*, consisting of hundreds of programs.

What you normally view as the 'desktop' is actually a file browser.  What you view as a menu bar is another little program that does just that.  In practice, you don't need any of that, since your local machine already has a desktop and a task bar.  All you need to do is run the remote program that you wanted to run directly, without clicking through the cluttered menus and it will then pop up on your local desktop.  Of course that requires that you actually know the name of the program that you want to run.

You can also run a file browser remotely to make it easier to see what is on the other machine:
$ ssh user@server nautilus

Once you figured out how to run a program remotely, you can make a little script on the local machine to launch it for you at the click of a mouse.

---

### Post by zobar on 2017-03-11
Thanks Herman!

It all works now!

---

### Post by oldos2er on 2017-03-11
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It'll help others who might be having the same problem.

Thanks.

---

