---
title: "Long boot, no splash, resolution off?"
date: 2008-04-17
forum: General Help
---

### Post by Redls1bird on 2008-04-17
Hey people.  Ive got a problem.  Ive got Ubuntu 7,10 installed on this machine, and the boot time is horrible.  Its over two minutes, but i havent timed it formally.  Also,  while booting, i dont have a ubuntu splash screen.  As well, the text displayed during boot is streched making me think the resolution is off.  I think all these might be related, but my resolution within the OS is ok. I dont know enough about Ubuntu or Linux to trouble shoot the long boot.  Any one got any ideas?

---

### Post by hariprs on 2008-04-17
* What is your system configuration?
* List the start up programs.

---

### Post by Redls1bird on 2008-04-17
Ill be honest, i dont know how to see what programs are scheduled to start in Ubuntu, Ill spare you the "i could do it in windows" speech. The system is a Dell latitude laptop with a p4 processor and 512 ram.  I dont remember the processor speed.

---

### Post by angry_johnnie on 2008-04-18
You could disable usplash, just to make sure there's nothing else slowing it down.

type:

```
gksu gedit /boot/grub/menu.lst
```

**After** the line that says ## ## End Default Options ## you'll be able to see all the menu entries.

So the first one should look something like this:

title           ubuntu, kernel numbers numbers  :-)
root          (hd0,0) or wherever it happens to be
kernel       lots of yadda yadda... :-)

Now, the line you're looking for is **kernel **.

Find the part where it says **quiet splash** and remove it.

Save the changes, and exit.

Now, when you reboot, you'll see lots of text instead of a splash image.

If it still hangs, then the problem was not really related to your usplash.  So, you should pay attention to all the text, and see exactly where it hangs.

---

### Post by Redls1bird on 2008-04-19
Johnnie, I followed your instructions and disabled the splash.  That was the problem, as my boot time has easily been cut in half now.  Thanks for the help.

---

