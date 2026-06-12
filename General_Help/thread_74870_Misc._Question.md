---
title: "Misc. Question"
date: 2005-10-12
forum: General Help
---

### Post by Tsboncompte on 2005-10-12
I have a question.

Is there some kind of program that allows for the user to give instructions to the computer to, say, shut down, or run a program, or so, under a certain trigger or at a certain time?

I have been looking for one but have found none... help will be appreciated
[RIGHT]
A Noob[/RIGHT]

---

### Post by dbott67 on 2005-10-12
The program **cron** is designed to do exactly what you want.  **cron** is a scheduler that will execute any given command (or script) on whatever frequency you desire.

Check the man files for cron to see how to use it & add it to your crontab.

If you have a specific example of what you want to do, post it here & I'm sure someone will show you what you need to add to your crontab file in order to get it to run.

-Dave

---

### Post by adwait on 2005-10-12
In case you don't like using command line interface, you can download Kcront to to it graphically:
```
sudo apt-get install kcron 
```

---

### Post by dbott67 on 2005-10-12
[QUOTE=adwait]In case you don't like using command line interface, you can download Kcront to to it graphically:
```
sudo apt-get install kcron 
```[/QUOTE]

Is kcron any better/worse than gcron?  I downloaded gcron (it was only a few kb; I was going to download kcron to compare, but it needed about 75 MB of dependencies & updates, so I decided to skip it :) )

-Dave

---

### Post by adwait on 2005-10-12
I don't remember using gcron.....but well, I am on Kubuntu so Kcron it is for me :)

Yeah, I guess kcron would require lots of dependencies on a non KDE machine, didn't quite realise that :)

---

