---
title: "Shutdown on event?"
date: 2006-10-31
forum: General Help
---

### Post by rozojc on 2006-10-31
Hi,

After spending the last two weeks trying other distros, I ended up going back to (k)ubuntu. I tried Zenwalk (really nice, but small repos), Arch (not my style), Frugalware (nice, I had some video problems), and finally came back...

Anyway, I was working the other day, and for some reason my computer started to overheat. The processor was running at 100%, fan was on, and temperature just increased and increased until I got worried and decided to turn it off. I know there is a bug like this with some laptops, but I don't think it's my case, as it has only happened once, and I have been unable to reproduce it. However, I installed ksensors, and I would like to configure it in such a way that if the temperature reaches a limit, it will automatically make my laptop shut down, instead of waiting for it to be extremely hot and having the mainboard halt the computer. Problem is that ksensors offers a way to "run a command" when a certain temperature is reached, but I can't just tell it to run "/sbin/shutdown now" because it would ask me for my root password, so it wouldn't really work automatically... What I want is to be able to run a command that will shutdown my computer WITHOUT asking anything, as the idea is that if I leave my computer on and I'm not around, it should be able to shut down on its own in case the temperature is too high...

any ideas?

---

### Post by volanin on 2006-11-01
Just a guess shot:

Create a custom startup script for it in /etc/init.d.
It will run as root, when your computer starts up, and then you can
call 'shutdown now' directly without worrying about the password.

---

