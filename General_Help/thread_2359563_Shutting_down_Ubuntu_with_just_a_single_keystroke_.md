---
title: "Shutting down Ubuntu with just a single keystroke or click?"
date: 2017-04-25
forum: General Help
---

### Post by xipho2 on 2017-04-25
Or even a better way to shut down the OS quickly? Thanks for suggestions!

---

### Post by pqwoerituytrueiwoq on 2017-04-25
In the power manager you can choose what the power button does for example shut down the system.
However, if you have cats they WILL turn your computer off while you are using it.

---

### Post by vasa1 on 2017-04-25
> **xipho2 said:**
> Or even a better way to shut down the OS quickly? Thanks for suggestions!
I would think "Shutting down Ubuntu with just a single keystroke or click?" a bit risky :)

I set up a short cut that requires pressing three keys together to generate a Y/N window so that I don't accidentally shutdown.

---

### Post by ajgreeny on 2017-04-26
If you really do want to go ahead with a keystroke for this in spite of the warnings you see above, all you need is a keyboard shortcut to the command **shutdown -h now**.

It no longer requires a password to shutdown, but be warned, as above that you should make it an unusual key combination or you could lose unsaved work.

Just for the record, I have a simple keyboard shortcut on my Xubuntu-16.04 to suspend using the *Pause/Break* key linked to command **xfce4-session-logout --suspend** and another to shutdown using *Winkey+Pause/Break* which used to be **xfce4-session-logout --halt** but is now simply **shutdown -h now** both of which still work without a problem in Xubuntu.

---

### Post by xipho2 on 2017-04-26
> **ajgreeny said:**
> If you really do want to go ahead with a keystroke for this in spite of the warnings you see above, all you need is a keyboard shortcut to the command **shutdown -h now**.

Sounds interesting. How is this done? I just installed Ubuntu on a flash drive, I have little experience with Linux. Typing this in the terminal..and then?

---

### Post by ian-weisser on 2017-04-26
> **xipho2 said:**
> I have little experience with Linux

Then please read about the[ difference between Linux, Windows, and OSX]("http://linux.oneandoneis2.org/LNW.htm"). It will save you a lot of frustration.

> **xipho2 said:**
> Typing this in the terminal..and then?
And then hit <enter>.

---

### Post by ajgreeny on 2017-04-26
But you can create a keyboard shortcut to the same thing but as I don't use Ubuntu I am not sure how you get to keyboard shortcuts; try searching with the dash, the top icon in the launchbar.

---

### Post by #&amp;thj^% on 2017-04-26
> **xipho2 said:**
> Or even a better way to shut down the OS quickly? Thanks for suggestions!

With older versions of Ubuntu Ctrl + Alt + Del will bring up options for shutdown, restart, suspend and hibernate. These can then be selected with the arrow keys and Enter.

**For a single hit solution in later versions you can use this script:** ([https://gist.github.com/chrisyco/988104](https://gist.github.com/chrisyco/988104)) to create a keyboard shortcut. First you need to download the script and save it on your computer. Next you need to make it executable by right clicking on it and going to properties &#8594; Permissions &#8594; Allow executing file as a program. Finally go to System Settings &#8594; Keyboard &#8594; Shortcuts &#8594; Custom Shortcuts and click the small plus symbol. For the command type in

```
/home/your-user-name/power.sh shutdown
```

or whatever path you saved the script to.

Suspend, hibernate and restart are also available by this method; just replace shutdown in the above command.

---

