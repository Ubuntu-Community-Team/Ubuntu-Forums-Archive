---
title: "Eclipse WTP and Java Stay in Memory"
date: 2007-02-05
forum: General Help
---

### Post by ethan@xmlstandards.org on 2007-02-05
Hello all,

I have a rather serious issue when using Eclipse WTP (Web Tools Project) on Ubuntu with the sun-java5-jdk from the multiverse repository.

I have firstly the issue that a .lock file is created in the workspace folder so that on subsequent eclipse relaunches the workspace is flagged as being in use.

I have been able to solve that by programmatically remove the .lock file upon each launch.

However for some reason eclipse itself seems to always stay in memory.

On a system like mine with 2 GIG of RAM I am quickly down to 512 RAM after a few launches.

Can anyone help?

Thanks

---

### Post by boredandblogging.com on 2007-02-05
Are there any errors when closing eclipse? Seems like Eclipse didn't close (and didn't remove the .lock). And then by removing the .lock by hand and starting Eclipse again, you have 2 instances of Eclipse running.

---

### Post by ethan@xmlstandards.org on 2007-02-07
Hi there,

Thanks for replying to me.

That is pretty much what is happening to me here. Eclipse is being closed and is for some reason staying in memory, the process is still up and running and a new process is created.

I have a 2 GIG memory allotment and after a while Eclipse will account for almost 1.4 GIG of memory.

No errors appear to be generated however.

Any clues.

---

### Post by boredandblogging.com on 2007-02-07
I'm not sure what the problem could be. Are you starting Eclipse from a terminal? I'd try that and see if shows any errors in the terminal when closing. I doubt any errors would be show any errors through the GUI.

---

### Post by hbobenicio on 2008-04-19
I'm facing the same problem. I'm using Ubuntu 7.10

I just downloaded the latest version of eclipse. Then I unzipped it and then I double-clicked the eclipse binary (I tried to run it on the terminal with a ./eclipse).

so then a quit eclipse, and until here everything works fine.

but the problem appears when I try to relaunch the eclipse. First, it tells me that the workspace is in use by another eclipse. So a remove the workspace/.metadata/.lock
and it works.

But the process of the first Eclipse instance is still im memory. And I just can't kill it because it's a "zumbi process". So to free that instance, I have to restart my system.

In resume: Eclipse doesn't appear to be closing in a correct way so the old instance (the process) is still in memory (or even running). Because of it, the old instance doen't unlock the current wokspace.

This is what I think about it.

Thanks in advance.

Hugo.

---

### Post by marcostoledo on 2008-04-28
Hi guys,

Has anyone found a solution for this yet? I'm running through exactly the same problem: 

I run eclipse through the terminal with:

"/usr/local/eclipse/eclipse&"

It starts without any problem the first time. When I close it, the proccess is still running if I run a "ps -ef", and it needs to by killed by hand.

For the guy here who was rebooting his workspace, you can do "killall -9 eclipse" to kill it so that it doesn't occupy your memory.

I also have ubuntu installed in ntfs through wubi in Ubuntu 8.04 ..can this be related?

Thanks,
Toledo

---

### Post by hbobenicio on 2008-05-07
I've tried to kill de eclipse process with killall and kill and Ubuntu's process manager... but nothing happens.

The eclipse process becomes a "zumbi" process, so I can kill it! :(

Thanks anyway...

I still don't having any clue to solve this problem...

Paciently,
Hugo.

---

### Post by kk_furtiva on 2008-05-12
I have the same problem.
Eclipse won't close, it stays in memory until I manually kill the process.

I'm using the Eclipse PDT All-in-One (downloaded from Eclipse.org) and Sun's Java6 from the repos.

Note: this only happens in my notebook (Ubuntu 8.04 Desktop), but on my other PC (Ubuntu 8.04 Server with Gnome) Eclipse closes as expected and it does NOT stays in memory.

Does anyone knows why is this happening? Any workaround?

Thanks,
Leandro

---

### Post by kk_furtiva on 2008-05-14
I've found that my problem is resolved if I use the Human theme (I was using Clearlooks)

weird...

Cheers,
Leandro

---

### Post by kk_furtiva on 2008-05-17
No. The problem was not solved. Today Eclipse started to stay in memory again and won't die until I manually kill it.

It's becoming pretty annoying...:mad:

Thanks,
Leandro

---

### Post by kk_furtiva on 2008-05-20
I've found this thread... 

[http://ubuntuforums.org/showthread.php?t=186977](http://ubuntuforums.org/showthread.php?t=186977)

I'll try this workaround at night

Thanks,
Leandro

---

### Post by kk_furtiva on 2008-05-23
I tried this solution and I think it actually works!

Excelent...! (Mr. Burns dixit)

Leandro

---

