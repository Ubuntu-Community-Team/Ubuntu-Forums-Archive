---
title: "ubuntu boots slower than windows"
date: 2008-06-09
forum: General Help
---

### Post by cnstarz on 2008-06-09
i can boot up to the windows login screen in about 20 seconds after grub, but ubuntu takes about at least a whole minute.  shutting down takes like 30 seconds with windows, and takes about a minute with ubuntu.  does anyone else experience this?

specs:
-dual boot with windows xp media center and ubuntu 8.04 32-bit(fresh install)
-amd x2 4400+
-2gb corsair value select ram
-eVGA 8800gtx
-asus a8n-sli premium mobo

---

### Post by bluepowder7 on 2008-06-09
win xp is surprisingly fast to boot.  noticeably faster than even win2k.  and faster than ubuntu 7.10.  but it crashes a lot more!

---

### Post by iaculallad on 2008-06-09
Install bootchart so we could see what's keeping Ubuntu slow on boot up.

```
sudo apt-get install bootchart
```

Restart/Reboot your Computer

```
sudo shutdown -r now
```

Attach the file /var/log/bootchard to your next post.

```
cat /var/log/bootchart
```

---

### Post by VMC on 2008-06-09
> **cnstarz said:**
> i can boot up to the windows login screen in about 20 seconds after grub, but ubuntu takes about at least a whole minute.  shutting down takes like 30 seconds with windows, and takes about a minute with ubuntu.  does anyone else experience this?

specs:
-dual boot with windows xp media center and ubuntu 8.04 32-bit(fresh install)
-amd x2 4400+
-2gb corsair value select ram
-eVGA 8800gtx
-asus a8n-sli premium mobo

LOL. This is almost the exact message I asked over at another Linux forum. You should have heard the commotion it caused. All I asked was how to speed up Linux and they kept hammering away at my 30 second XP startup. Saying I was lying and show me your results, etc, etc.

The sad thing is I was only using Windows as an example and how can I speed up Linux boot time.

You already got a good reply in installing "bootchart".

By the way, mine boots up in about 45 seconds. I know I can trim out some services, but I like the idea of "bootchart"

---

### Post by iaculallad on 2008-06-09
Also, you could try browsing this [thread]("http://ubuntuforums.org/showthread.php?t=89491") about "Speeding up Ubuntu Boot process".

---

### Post by Tanjer1588 on 2008-06-09
When i was useing 7.10 it booted pritty fast i had no problems with it but once i moved to 8.04 it took like a whole min to boot as well... i dont know what the deal was but since i moved to 8.04 i have been running into a lot of kinks

---

### Post by VMC on 2008-06-10
> **iaculallad said:**
> Install bootchart so we could see what's keeping Ubuntu slow on boot up.

```
sudo apt-get install bootchart
```

Restart/Reboot your Computer

```
sudo shutdown -r now
```

Attach the file /var/log/bootchard to your next post.

```
cat /var/log/bootchart
```

Okay here's mine. It says 31 seconds, but in real time its around 46 seconds:

EDIT: Do I have to unintall bootchart. Is it going to add to my boot time?

---

### Post by jimv on 2008-06-10
The Vista install on my desktop boots in about 20 seconds.  

Crazy...

But I prefer Ubuntu because IT DOES WHAT I WANT IT TO DO.

---

### Post by Pjotr123 on 2008-06-10
Sometimes boot time can be reduced by working around this bug:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 3 )

Note: boot time should be measured from the moment that the BIOS screen appears, until the moment that a *fully functional* desktop has appeared. With all services started.

In Ubuntu, it's only fully functional a couple of seconds (about 5) after the appearance of the desktop. In Windows this lasts much longer, among other things because the antivirus app updates itself. You have to wait until it's finished. 

So that story of Vista in 20 secs is, well, "not based on the facts" (to put it very mildly). :)

Greeting, Pjotr.

---

### Post by jimv on 2008-06-10
> **Pjotr123 said:**
> 
In Ubuntu, it's only fully functional a couple of seconds (about 5) after the appearance of the desktop. In Windows this lasts much longer, among other things because the antivirus app updates itself. You have to wait until it's finished. 

So that story of Vista in 20 secs is, well, "not based on the facts" (to put it very mildly). :)

Actually, it IS based on the facts.  I keep my Windows machines very lean.  No antivirus, no firewall (my router takes care of that), no MS Office starting up automatically, no unneeded services running, no programs starting that don't need to...it takes 20 seconds from when Vista starts booting.  Maybe 30 from the appearance of the bios screen.

---

### Post by jreikes on 2008-06-10
I'll chime in that although I almost never boot to Vista, it does boot MUCH faster than my Hardy boot.  Even if you wait for the processes that Windows is still working on when the desktop first appears, I'm still up and running WAY faster.  It's not even close, probably 1/3 the time.

That said, I still use Ubuntu 99.99% of the time now, but I would definitely like to speed up my boot.

---

### Post by jimv on 2008-06-11
I managed to get Ubuntu to load a bit faster by disabling some services and adding the word "profile" to the end of the kernel line in Grub (don't edit your menu.lst file, just press E on the Grub boot screen to edit the line temporarily)

---

### Post by Pjotr123 on 2008-06-11
> **jreikes said:**
> I'll chime in that although I almost never boot to Vista, it does boot MUCH faster than my Hardy boot.  Even if you wait for the processes that Windows is still working on when the desktop first appears, I'm still up and running WAY faster.  It's not even close, probably 1/3 the time.

That said, I still use Ubuntu 99.99% of the time now, but I would definitely like to speed up my boot.

This may help:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)

(number 3 )

---

