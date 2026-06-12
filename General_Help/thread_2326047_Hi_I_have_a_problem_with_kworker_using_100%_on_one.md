---
title: "Hi I have a problem with kworker using 100% on one of the core.  16.04"
date: 2016-05-27
forum: General Help
---

### Post by jcer93705 on 2016-05-27
Hi I have Ubuntu Mate 14.10 running cinimume but is the same with mate same issue. One of the core is 100 percent sometimes 99 and it is caused by kworker. How can I fixed this? It lags and
I'm tired of seeing this type of problem with linux. Trying to move away from Windows but this type if this can be solved I would be happy. Ty

---

### Post by howefield on 2016-05-28
If ti were mine, I'd start with the answer from tanius in this askubuntu[ thread]("http://askubuntu.com/questions/33640/kworker-what-is-it-and-why-is-it-hogging-so-much-cpu")...

---

### Post by yazdzik-k on 2016-07-16
Dear Howe,

Same problem here.  Now from that thread,  which would indeed explain which process is hogging:

[COLOR=#111111][FONT=Ubuntu] (On Ubuntu, this needs you to login with [/FONT][/COLOR]sudo -s[COLOR=#111111][FONT=Ubuntu]).

not sure,  and I have run debian for many years,  how to do this

had I life to live over,  I would have created a root account,  but fear doing so now would kill all my gksu stuff... 

so I need to run:
[/FONT][/COLOR]```
echo l > /proc/sysrq-trigger
```   
 and have no way of so doing,  as it does not work by prefacing sudo

[COLOR=#111111][FONT=Ubuntu]best,

martin


[/FONT][/COLOR]

---

### Post by yazdzik-k on 2016-07-18
More info:  grepping the interupts gives
```


/sys/firmware/acpi/interrupts/sci: 2389231




/sys/firmware/acpi/interrupts/gpe61: 2389235   enabled


/sys/firmware/acpi/interrupts/gpe_all: 2389261


```

now I cannot save any file using gedit via sudo,  as it will not allow me to "save anyway"  when it cannot copy the file to a backup...

had I to do the install over,  I would create a root account.

now, what simple steps can be taken to fix this?

[http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high](http://askubuntu.com/questions/176565/why-does-kworker-cpu-usage-get-so-high) seems to indicate a solution,  but I am not sure how to implement it.

in case anyone reads this,  

```

sudo -s
echo "disable" > /sys/firmware/acpi/interrupts/gpe61

```

did it, as for new ubuntu users, used to the debian having a real root, sudo -s as the first command gives one a real root terminal.  It should not have have to requires so much research,  and proves that having a real root account,  while less secure,  is  a different way s of doing it.

I suspect editing crontab to make this permanent will work fine now.

It thus seems that finding the acpi interrupt and disabling works,  at least for my situation,  and I hope noting how to use sudo more effectively will help people coming to Ubuntu from debian.

Thanks for everyone's patience



best wishes,
M

---

