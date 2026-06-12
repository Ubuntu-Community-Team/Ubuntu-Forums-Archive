---
title: "Automatic Startup/Shutdown"
date: 2008-06-19
forum: General Help
---

### Post by izrafeel on 2008-06-19
Hi,

I'm looking for an easy way to configure my machine to automatically turn-on and turn-off at predefined times on a daily basis.  For example, how would I set it up so that it turns-on at 8am and turns-off at 6pm, Monday to Friday?

I'm still relatively new to Ubuntu to any help would be much appreciated.

Thanks.

---

### Post by geo909 on 2008-06-19
The turn **off** thing is quite simple. You use the *shutdown* command.
Do
```
man shutdown
```
for the options.

You should do your job with something like
```
sudo shutdown -hP 18:00
```

Now, for doing that on a daily basis, you should probably arrange 
a cron job. Cron executes commands that you tell it in given periods
of time. See 

```
man cron
```

I have never used cron so I am not sure what happens with commands
that require root privileges, like *shutdown*. The only way to find out is to make a little test with cron.

 I doubt it there is an option for powering the machine on.
Since it's off, there's nothing that can be executed.
But I'm not sure. Maybe there will be a thing with some 
kind of standby option..

---

### Post by izrafeel on 2008-06-21
Thanks for the reply.  I think in the limited case, shutdown-only will suffice.  I'll check out the cron job option.

---

