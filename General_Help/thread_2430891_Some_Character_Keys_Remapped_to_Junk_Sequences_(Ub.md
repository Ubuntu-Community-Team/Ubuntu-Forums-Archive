---
title: "Some Character Keys Remapped to Junk Sequences (Ubuntu 18.04)"
date: 2019-11-08
forum: General Help
---

### Post by akathehidden on 2019-11-08
I am running Ubuntu 18.04 on a Lenovo ThinkPad E555 laptop.

A few weeks after the installation, some (but not all) of my keys have suddenly become "remapped" to "junk sequences". Specifically, the i, k, and comma keys.

When I press i, the sequence `q*ew6r` is printed. When I press k, the sequence `a7ds2fjk` is printed. This problem persists after reboot and occurs in all applications.

I have ruled out a hardware issue, as my Win 10 dual boot works fine. After reinstalling Ubuntu 18.04, the keys worked fine again for some time, but the problem has now recurred for a second time.

I have tried the following:

[LIST]
[*]Resetting the console and keyboard configuration: `sudo dpkg-reconfigure -plow console-setup` and `sudo dpkg-reconfigure keyboard-configuration`.
[*]Verifying that I do not have conflicting keyboard layout and language settings.
[*]When I execute `showkey -k` to test my keyboard, pressing the i and k keys register the same key sequences that I gave above.
[*]I verified num lock is off
[*]I booted into a live CD, and the i,k, and comma keys work correctly.
[/LIST]

Given the above troubleshooting, I believe that some sort of configuration has been corrupted, perhaps by a package update?

I understand that there are many layers between a keypress and the final processing of that keypress, and I would appreciate some guidance about how to troubleshoot this.

Thank you for your help - both for this issue (my first actual post!) and for all the fantastic responses to other posters that have helped me over the years.

---

### Post by mörgæs on 2019-11-10
Hi, welcome to the fora.

> **akathehidden said:**
> After reinstalling Ubuntu 18.04, the keys worked fine again for some time, but the problem has now recurred for a second time.


How does it work if you do a fresh install of 19.10?

---

### Post by akathehidden on 2019-11-18
After upgrading to 19.1 using the system's update utility, the problem still persists.

I suspect that a fresh install from a 19.10 live CD would correct the problem, as this issue has reoccurred for me a second time after reinstalling 18.04 from a live CD. However, I suspect it may likely reoccur for a third time in 19.1, since the problem mysteriously began a few days after installation of 18.04 (in both cases).

Do you have any ideas about what configuration files I should investigate?

I think we can narrow the configuration files down since we know a fresh install corrects the problem, while a system upgrade does not!

Thanks!

---

### Post by mörgæs on 2019-11-18
I don't know which configuration files to check and/or edit. 
While you are waiting for someone to answer I guess that you have plenty of time to try a clean install of 19.10 :-)

---

