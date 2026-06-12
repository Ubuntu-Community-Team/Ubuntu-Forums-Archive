---
title: "Kill All Running Apps"
date: 2022-02-05
forum: General Help
---

### Post by Quarkrad on 2022-02-05
I have a neighbour that I've just installed xfce/xubuntu. She is in her 80s and cannot get her head around closing desktop apps down before shutting her machine down - she presses and holds to power button on her pc and just crashes the machine!   I'm looking at providing her with a launcher/icon that she can press to shutdown.  I'm happy with something like *shutdown now* in a bash script but what (kill?) command can I use to shutdown any running app.  So far my searches have required knowing the name of the app or the pid number.   Is there a command that will kill all running apps that I can use before running the *shutdown now* command where I do not know what desktop apps are running?

---

### Post by yetimon_64 on 2022-02-05
> **Quarkrad said:**
> *.. now* in a bash script but what (kill?) command can I use to shutdown any running app...

[s]For "kill" you could try...
```
kill -9 -1
```[/s]
From "man kill"...
> ```
       kill -9 -1
              Kill all processes you can kill.

```

**Edit**: I just noted "I've just installed xfce/xubuntu" in your post and being on Xubuntu 20.04 I tested the above command. It works but may be too much for your needs as it sends me out and onto a login screen. In a script it will kill the script it is running from most likely; I don't think it will be of much use in your case so have struck it out but left it visible if you wish to test as well.

**Edit 2**: If you do use that command in a script and your neighbour ends up on the log in screen, you would need to teach her to then click on the power menu icon on the top panel and select the "shut down" option; so it may still be usable.

---

### Post by Quarkrad on 2022-02-05
Yes - thank you, I discovered that.  It looks to me that xcfe does not allow this. Sort of .... help!

---

### Post by dragonfly41 on 2022-02-05
These notes might help.

[https://www.freecodecamp.org/news/linux-list-processes-how-to-check-running-processes/](https://www.freecodecamp.org/news/linux-list-processes-how-to-check-running-processes/)

Personally I favour automation scripts using Actiona (in the repo).
There is a kill process (Qt) widget and if you create a javascript list of apps you can loop through them
to kill them all.

---

