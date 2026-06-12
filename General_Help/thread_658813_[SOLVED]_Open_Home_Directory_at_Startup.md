---
title: "[SOLVED] Open Home Directory at Startup?"
date: 2008-01-05
forum: General Help
---

### Post by Tsi99 on 2008-01-05
Is there a way to open the Home directory in Nautilus at boot?

I tried adding the following entries as commands in the gnome sessions start up tab.   Neither worked.

nautilus $HOME/
nautilus

Thanks,
Matt

---

### Post by ntowakbh on 2008-01-05
I just tried this and it worked for me:

System-->Preferences-->Sessions

Then clicked add for start up programs, and added the command

'nautilus /home/[username]/'

of course, you should replace "[username]" :)

---

### Post by Tsi99 on 2008-01-05
I tried that and it did not work for me.  I'm running 7.10.  What version of Ubuntu are you running?

What I find disturbing is that I can run the command from terminal and it works.

Maybe something is interfering with it.  Besides normal start up stuff I have the following load during start up.

Thunderbird
Firefox
Brightside
Devil's Pie

Any Ideas?

---

### Post by mdebusk on 2008-01-05
> **Tsi99 said:**
> Is there a way to open the Home directory in Nautilus at boot?

Try using "[gnome-open]("http://ubuntu.wordpress.com/2006/12/16/gnome-open-open-anything-from-the-command-line/")" instead of "nautilus", i.e.:
```
gnome-open /home/USERNAME
```

---

### Post by ntowakbh on 2008-01-05
> **Tsi99 said:**
> I tried that and it did not work for me.  I'm running 7.10.  What version of Ubuntu are you running?

What I find disturbing is that I can run the command from terminal and it works.

Maybe something is interfering with it.  Besides normal start up stuff I have the following load during start up.

Thunderbird
Firefox
Brightside
Devil's Pie

Any Ideas?

I doubt it has anything to do with Thunderbird of Firefox, I've never heard of the others, so not sure. I am also using 7.10.

---

### Post by Tsi99 on 2008-01-06
> **mdebusk said:**
> Try using "[gnome-open]("http://ubuntu.wordpress.com/2006/12/16/gnome-open-open-anything-from-the-command-line/")" instead of "nautilus", i.e.:
```
gnome-open /home/USERNAME
```

That worked, Thanks

---

### Post by mdebusk on 2008-01-07
> **Tsi99 said:**
> That worked, Thanks

Glad to be of help.

Remember to mark the thread as solved. :)

---

### Post by Tsi99 on 2008-01-07
> **mdebusk said:**
> Glad to be of help.

Remember to mark the thread as solved. :)

Do I just change the title or is there another way to mark the thread as solved?

---

### Post by mdebusk on 2008-01-11
> **Tsi99 said:**
> Do I just change the title or is there another way to mark the thread as solved?

Above the thread there's a menu labeled "thread tools". It's in there.

Anyone searching for the same solution from now on will know your thread has the answer.

---

