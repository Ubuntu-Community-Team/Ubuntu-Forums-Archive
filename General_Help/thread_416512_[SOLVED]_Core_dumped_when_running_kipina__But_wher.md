---
title: "[SOLVED] Core dumped when running kipina?  But where?"
date: 2007-04-21
forum: General Help
---

### Post by mojoman on 2007-04-21
I'm running Xubuntu Feisty 64-bit and when I installed Kipinä (or kipina as I understand it is written in languages not endowed with enough letters ;)  ) seemingly without any problems. However, when I try to start it in GUI nothing happens so I switch to CLI and try there. I get the following output:
```

Segmentation fault (core dumped)
```

Now, earlier on I ran Ubuntu Dapper64-bit and had the same problem but then I also had a 32-bit chroot environment so I didn't bother about it and just installed in there, where it ran just fine. However, this time around I want to get by without a chroot so now I actually have to deal with this problem.

So, my first question is: where is the core dumped? I bet it's just eating up my HD-space somewhere :mad: 

Second question would obviously be: are there any known fixes for this? I tried google and wikipedia but let's face it, Kipinä doesn't seem to be the worlds most used program and there is very little information on it. As for general information on core dumps and segmentation faults, I'm really totally lost when it comes to programming. 

Most likely, it should be reported as a bug but I would like to be able to report with some more info (the dumped core would probably be a good help to someone debugging this).

Any ideas, anyone?
/mojoman

---

### Post by mhansen on 2007-04-22
check /var/crash/


Regards,
Mike

---

### Post by mojoman on 2007-04-22
> **mhansen said:**
> check /var/crash/


Regards,
Mike

Yup, there it was. Thanks. The log didn't tell me anything though but that was expected. I'll probably report it as a bug to the developer and include the log file.

---

### Post by studo77 on 2007-11-05
> **mojoman said:**
> Yup, there it was. Thanks. The log didn't tell me anything though but that was expected. I'll probably report it as a bug to the developer and include the log file.

And adding [SOLVED] is not the right way. You may have found your logfile, but kipina is not running.

---

