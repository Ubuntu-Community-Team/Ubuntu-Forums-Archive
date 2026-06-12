---
title: "fstab mac mount not working with new mac share?"
date: 2013-03-04
forum: General Help
---

### Post by cbanakis on 2013-03-04
Hopefully someone can figure this out, because it makes no sense to me.

This is my original fstab line that has been working for years.
```
//192.168.99.95/My\040Docs /home/chris/M13-Docs cifs uid=chris,credentials=/etc/cifspw
```

I am replacing the Mac, that this line points to.

I setup everything the same exact way, except with the new ip.
```
//192.168.99.99/My\040Docs /home/chris/M13-Docs cifs uid=chris,credentials=/etc/cifspw
```

But for some reason it will not work with the new server.

```
sudo mount -a
mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

Does anyone know what could possibly be different that causes this not to work with the new mac share?

Thanks in advance

---

### Post by cbanakis on 2013-03-04
After further research, it looks like the problem is that the new mac has Mountain Lion installed.

And from Lion on, Macs use smbx instead of smb.

So I guess my question is, how do I mount an xmbx share via fstab?

---

### Post by cbanakis on 2013-03-06
Ok, I am finally getting somewhere.

I added the following options to fstab
```
nounix,sec=ntlmssp
```

So now it looks like this
```
\\192.168.99.99/My\040Docs /home/chris/M13-Docs cifs uid=chris,credentials=/etc/cifspw,nounix,sec=ntlmssp
```

Now if I ```
sudo mount -a
``` everything seems to be in order.

However, it is not mounting automatically on startup for some reason?

So I can now permanently mount the share, but I need to do it with ```
sudo mount -a
``` in terminal, every time I power on my computer?

Any thoughts on that?

Thanks

---

### Post by Morbius1 on 2013-03-06
It could be the reemergence of a very old bug where fstab is read and executed before the network is up, fails for the cifs mount, and never goes back.

What I suggested back then was to make your workaround permanent:

Add a file to if-up.d:
```
gksu gedit /etc/network/if-up.d/remount
```
With this content:
```
#!/bin/sh
mount -a
```
Make the file executable:
```
sudo chmod +x /etc/network/if-up.d/remount
```
Anything in if-up.d will execute only after your network is up.

---

### Post by cbanakis on 2013-03-07
Thanks for your post.

It did not work, though I did finally get it working.

Just to be clear though, this is not a linux, or fstab related bug.

This is because Apple decided they can make a better samba than the one that has been perfected over the last 20 years.  And boy were they wrong.

This issue expands far beyond Ubuntu.

Since I got Mountain Lion up and running (Upgraded from Snow Leopard)

No Windows computers have been able to connect to the Mac shared folders.
No Linux computers have been able to connect to the Mac shared folders.
No Android devices have been able to connect to the Mac shared folders.

Everything worked fine with Snow Leopard, but that was before Apple decided to fix samba.

Now Ubuntu computers are all connecting perfectly.

I added the options 'user' and 'auto' to my fstab, and all is well.

```
 //192.168.99.99/My\040Docs /home/chris/M13-Docs cifs uid=chris,credentials=/etc/cifspw,nounix,sec=ntlmssp,user,auto
```

Thanks Apple.

If you left everything alone, I might have gotten something productive done over the last 2 weeks.

Thanks to you, I managed to acomplish nothing other than getting everything to work like it used to.

Windows connections are still sketchy, and Android simply will not work, unless Apple fixes it from their end.

But all my Ubuntu needs are met, for now.

---

### Post by cbanakis on 2013-03-07
Ok, new problem.

How do I mark this thread as solved?

Used to be under thread tools, but not anymore?

---

### Post by capscrew on 2013-03-07
> **cbanakis said:**
> Ok, new problem.

How do I mark this thread as solved?

Used to be under thread tools, but not anymore?

See this: [**_[COLOR="#FF0000"]http://ubuntuforums.org/showthread.php?t=2121377[/COLOR]_**]("http://ubuntuforums.org/showthread.php?t=2121377")

It seems lots of things are broken these days.

---

### Post by cbanakis on 2013-03-08
Thanks.

I guess Ubuntu Forums are following Apples example, and fixing things that were not broken.

:)

---

### Post by ChrisShUK on 2013-05-17
> **cbanakis said:**
> Ok, I am finally getting somewhere.
I added the following options to fstab
```
nounix,sec=ntlmssp
```

Thank you :)
This has been a pain in the a**e for the last few hours, and this sorted it :)

---

