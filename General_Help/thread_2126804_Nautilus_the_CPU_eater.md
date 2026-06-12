---
title: "Nautilus the CPU eater"
date: 2013-03-18
forum: General Help
---

### Post by woollypigs on 2013-03-18
Hi

Not sure where to put this, so Mods please move to the right place.

I upgraded from Ubuntu 11.10 to 12.10 (64bit) and since then upon start up Nautilus just sits there and eat the CPU and memory and makes the laptop pretty unusable. 

I have to do a "killall nautilus" in the terminal to get control over laptop again. I have even tried to upgrade to 13.04 (which runs great on my laptop) and even upgraded Nautilus to 3.6 but sill it hangs.

I even tried "sudo apt-get purge nautilus-open-terminal" but Nautilus is still eating CPH.

I have looked around and yet to find a solution that solves it and I can see others are having the the same problem.

I'm now using Gnome-commander and terminal for my files. Though every time I boot up, insert a external HDD or when other programs calls for Nautilus I end up with a laptop that unusable until I kill nautilus, which is rather annoying to do.

Does anyone here got an idea on how to solve this. I used to like Nautilus but I might have to give Gnome etc a go to stop this.

Laptop : Dell 13z (1.2Ghz,3Gb Ram, 500Gb HDD)

---

### Post by ibjsb4 on 2013-03-18
Have you tried opening nautilus from terminal?  May give you some useful info.

---

### Post by woollypigs on 2013-03-18
Hi and thanks

Here is the output of "sudo nautilus"

Initializing nautilus-dropbox 1.4.0

(nautilus:25693): IBUS-WARNING **: The owner of /home/ymer/.config/ibus/bus is not root!
Nautilus-Share-Message: unknown format for key 'Public/usershare_acl' as it contains 'S-1-1-0:F,'.  Assuming that the share is read-only

And that is where it hangs

I just tried to remove dropbox and now it just hangs and this comes 

"Could not register the application: Timeout was reached"

---

### Post by Yellow Pasque on 2013-03-18
I think you want 'gksu nautilus' (use gksu instead of sudo for graphical programs)

---

### Post by ibjsb4 on 2013-03-18
```
killall dropbox
``` do anything?

---

### Post by rnerwein on 2013-03-18
hi
--> I think you want 'gksu nautilus' (use gksu instead of sudo for graphical programs) 				<---
i know that's a lot of work - but sudo must handle this behavior (i know that sudo is penauts again kernel development).
sorry - but this no answer for me - it looks like a bug !!!
exception handling is the salt of programing.
ciao

---

### Post by VanillaMozilla on 2013-03-18
No, you do need to use gksu instead of sudo for GUI programs.  Otherwise you run into strange side effects -- file ownership problems, if I recall.  I don't really know, but it may well have something to do with the error message.

But actually, you probably shouldn't use either sudo or gksu. I can't think why you would need to start Nautilus as a super-user in this case.

---

### Post by mörgæs on 2013-03-18
How much have you up- and downgraded the system since initial installation? It sounds like a lot of experiments have been going on.

---

### Post by woollypigs on 2013-03-18
Thanks all, sorry for the delay, life called :)

>killall dropbox
>dropbox: no process found

>gksu nautilus 
I was asked for my password in a "gui" popup and after awhile nothing happened just went back to the prompt.

I have only upgraded, not downgraded, from 11.10 to 12.10 to 13.04 and Nautilus to 3.6 to 3.8

When I use the "gui" and click on files(as it is called in 13.04) it starts up, in the sense that it will show a grey window and the CPH is at 100% and memory used is slowly getting more and more.

---

### Post by mörgæs on 2013-03-18
I would go straight to a reinstall of 13.04, keeping the standard Nautilus.

---

### Post by woollypigs on 2013-03-18
Well I upgraded from 12.10 to 13.04 because of the issues with nautilus in 12.10 :)

Might just insert a script upon start up to kill nautilus, that should sort it for now. Since 13.04 is running just fine as long as Nautilus isn't running.

---

### Post by mörgæs on 2013-03-19
The problem is likely not the version(s) you are using but the upgrade process itself. A clean install is worth trying.

---

### Post by woollypigs on 2013-04-09
Finally had time to reinstall the system. Had a stab at Mint to to see if that would work better, though it worked great from the USB but on at all from the HDD.

Now back on 12.10 and Nautilus is behaving just fine and I can use Ubuntu again, fast and stable. 

Thanks

---

