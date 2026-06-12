---
title: "Shut down does not work"
date: 2008-06-30
forum: General Help
---

### Post by mikerobinson on 2008-06-30
After upgrading to 8.04, I am unable to shut the computer down. When I tell it to "Power Off", I see the Kubuntu logo and the blue bar disappears to the right and then it just sits there indefinitely. To shut it off, I have to push ctrl-alt-delete, which does some things and then reboots the computer and then hold down the power button to turn it off. This is very inconvenient. When it is held in that state, if I push ctrl-alt-F7, I see a message saying> /etc/init.d/rc: 317: /etc/rc0.d/S90halt: not foundHowever, I can see that the file is definitely there:
> lrwxrwxrwx   1 root root   14 2007-09-30 07:29 S90halt -> ../init.d/halt
And /etc/init.d/halt is there as well. I can even open S90halt in a text editor just fine.
> -rwxr-xr-x   1 root root  1305 2008-06-15 01:13 halt

Any suggestions would help. This problem didn't exist in 7.10, but only appeared after I upgraded to 8.04.

Thanks.

---

### Post by mikerobinson on 2008-07-02
Bumpppppp

---

### Post by cariboo on 2008-07-02
Just to check that the problem isn't elsewhere, can you switch to a console Ctrl-Alt-F1 and use one of the following commands:

```
sudo halt
shutdown -h now
```

Jim

---

### Post by mikerobinson on 2008-07-03
Thanks for your reply. Both of those commands have exactly the same effect. Neither of them actually shut the computer down. I'm wondering if it has something to do with the fact that I originally installed probably version 6.04 and upgraded it every release (even a couple of beta releases) up to 8.04. Over the past couple of years I've done a lot of playing around. Maybe it's just time for a reinstall. I hope not though.

---

### Post by p_quarles on 2008-07-03
Well, you could also try the most brute force way of shutting down (short of the power button). The command is:
```
sudo telinit 0
```
I don't know if that will do anything either, but worth a try. Make a note of any error messages and post them here.

---

### Post by mikerobinson on 2008-07-03
This also has the same effect. I am not receiving any error messages anymore though. It could be that since I updated my display driver that I am no longer getting the S90halt not found error like I used to. I looked through some of my log files, but I didn't see anything special. If you want me to paste a section of them here, I can do that. Just let me know which one(s).

---

### Post by mikerobinson on 2008-07-08
I guess the only thing left to do is reinstall kubuntu then :(

---

