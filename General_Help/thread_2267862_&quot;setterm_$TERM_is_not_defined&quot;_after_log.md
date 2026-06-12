---
title: "&quot;setterm: $TERM is not defined&quot; after login"
date: 2015-03-04
forum: General Help
---

### Post by Angel_Candelaria on 2015-03-04
Hi all.

After logging in to Lubuntu 14.04, I'm getting this message:

```

Error found when loading /home/username/.profile:

setterm: $TERM is not defined

As a result the session will not be configured correctly.  You should fix the problem as soon as feasible.

```

I tried doing a search for this error message, but the solutions I found doesn't seem to apply in my case (for example, [this one]("http://unix.stackexchange.com/questions/185665/error-while-booting-ubuntu-14-04-setterm-term-is-not-defined") seems to be similar to my case, but it doesn't really offer any solution to it).  It is refering to my .profile file, but I don't really know what to do to prevent this message from appearing after logging in.

What should I do in this case?  Thanks in advance for any help.

---

### Post by steeldriver on 2015-03-04
Hello and welcome to the forums

Have you added anything non-standard to your .profile file? what is the result of the command

```

diff /etc/skel/.profile /home/username/.profile

```

---

### Post by Angel_Candelaria on 2015-03-05
Thanks for your reply, steeldriver.

I ran the command as you suggested, and discovered that my .profile had some extra instructions.  They seem related to some sort of power management software I may have installed at some point, then removed:

```


xset -dpms
xset s off
setterm -powersave off -blank 0



```

I guess the error message was triggered by the last instruction.  Anyway, I removed those three lines.  Problem solved.

Thanks you very much.

---

