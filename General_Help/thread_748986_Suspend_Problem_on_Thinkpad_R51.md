---
title: "Suspend Problem on Thinkpad R51"
date: 2008-04-08
forum: General Help
---

### Post by samgurung on 2008-04-08
Hi all,

I have fiesty fawn installed on a Thinkpad R51... My problem is the Fn + F4 key does not work. Its supposed to suspend the machine but nothing happens. All other thinkpad keys work fine. Also if I add a vga=791 line to my boot options in grub... my notebook does not suspend correctly. It suspends but while resuming i cannot open any windows and the machine becomes very slow. Has anyone faced a similar situation or has a solution???

---

### Post by Red Baron on 2008-04-08
You may want to try installing the "tpb" package which is supposed to enable special keys on thinkpads. It fixed the Fn+F2 lock screen issues on my R61 in Hardy. 

```
sudo apt-get install tpb
``` 

Otherwise, I suggest looking through the ThinkWiki page about special keys:
[http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work]("http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work")

---

