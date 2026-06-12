---
title: "vmware stopped working after last kernel upgrade"
date: 2006-07-19
forum: General Help
---

### Post by tgrzejsz on 2006-07-19
Hi,
After last kernel upgrade vmware modules don't load anymore. The message when trying to start vmware looks like this:

Starting VMware services:
   Virtual machine monitor                        failed
   Virtual ethernet                               failed
Module vmnet is not loaded.  Please verify that it is loaded before
running this script.

I'am using vmware installed from Dapper packages. Reinstalling doesn't help.

Thanks for help,
Tomek

---

### Post by philippe_carlo on 2006-07-19
You have to re-install VMWare after every kernel upgrade. Don't worry, it does not break your virtual machines. I keep the VMWare installation files on my system because of this. I thionk this is mentioned in the README, though.

---

### Post by PriceChild on 2006-07-19
you don't have to completely reinstall... you just have to re-run the vmware-config.pl file to remake a kernel module to assist with its running.

---

### Post by tgrzejsz on 2006-07-19
> **philippe_carlo said:**
> You have to re-install VMWare after every kernel upgrade...

Thanks for the answer. But looking at my post I see that I've mentioned that reinstalling doesn't help. I've tried it several times, really it doesn't.
Maybe the fact that I'am using vmware from Dapper repositories is significant here? I'am not using a tar file from vmware site.

Greetings,
Tomek

---

### Post by philippe_carlo on 2006-07-19
True, but it takes the same amount of time. Actually, it would be nice to find a way to just recompile the modules without VMWare asking all these questions over again. That, said, I'm not a perl expert ;-)

---

### Post by x64Jimbo on 2006-07-19
Actually since all it does is ask you if you want to keep the same settings from last time, it would be cool if you could pass it a bunch of "enter, enter, enter" commands so it would finish in a couple seconds. It's really not that much of a hassle though...

---

### Post by philippe_carlo on 2006-07-19
> **tgrzejsz said:**
> ...
Maybe the fact that I'am using vmware from Dapper repositories is significant here? I'am not using a tar file from vmware site.
...


I had troubles with the dapper-release too. I'm using VMWare's distro without the slightes problem, though. Make sure to remove the dapper package first!

---

