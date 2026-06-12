---
title: "somes issues with  16.04"
date: 2016-11-16
forum: General Help
---

### Post by christon74 on 2016-11-16
Good evening fellow Ubunters

When I click on any of my favourites, three tabs open instead of just one_ and this happens very often. Browser: Mozilla Firefox.
When I send an e-mail with Thunderbird, it does shut down of its own accord quite often too. 
when I want to print any document _saved to my hard disk, or print a webpage_ only the first six lines are printed and the rest of the sheet is blank. This is why I have to reboot and resort to Vista (I'm on dual boot) to print anything. 

None of the above phenomena ever happened with ubuntu 14.04 and I am still very much grieving it.

---

### Post by Bucky Ball on 2016-11-16
Please do this in a terminal.

```
sudo apt autoremove
sudo apt update
sudo apt full-upgrade
```

The last command will *not* upgrade your release to 16.10. ;) 

Please post any and all errors any of those commads spits out. Please use [code] tags for terminal output. See green link in my signature below for how if you don't know how. If it throws no errors, reboot the machine and see if problems persist and report back.

There is either 'one big problem' or you have posted a lot of seperate ones. If the latter, you would be better to post separate threads for each, but let's see what those commands spit out first.

---

### Post by christon74 on 2016-11-17
Thank you Bucky Ball ;) _ I've just rebooted. The terminal threw no error at all, or so it seems to me. And yes, I reported several problems in just one post, out of frustration. Next time, I be a good boy and post separate threads. Promise. If problems persist, then I guess I'll only have to sigh and bend my head with resignation.....

---

### Post by Bucky Ball on 2016-11-17
> **christon74 said:**
> Thank you Bucky Ball ;)Next time, I be a good boy and post separate threads.

Nothing to do with that. It's about the most effective way to post to get the quickest response and fix for your problem. More than one issue per thread just gets confusing. ;)

> **christon74 said:**
> Promise. If problems persist, then I guess I'll only have to sigh and bend my head with resignation.....

Just edit the title, edit the other questions out of the first post and continue trying to fix the Firefox issue. You haven't really started yet. If you have no action after 12 or so hours, just post 'bump' in a new post on the thread.

---

