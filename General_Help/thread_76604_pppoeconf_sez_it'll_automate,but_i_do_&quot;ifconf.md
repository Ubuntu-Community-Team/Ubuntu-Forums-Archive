---
title: "pppoeconf sez it'll automate,but i do &quot;ifconfig eth0 up&quot; &quot;pppoeconf&quot; in every reboot"
date: 2005-10-15
forum: General Help
---

### Post by hanzj on 2005-10-15
Hello,

When I was using hoary, I had to do "sudo pppoeconf" only once and whenever I rebooted/restarted my computer, I had no trouble connecting to the internet. I just had to open up the program (xchat, web browser, etc.) and all was ready to go.

I recently upgraded to breezy. Whenever I restart/reboot, the internet connection seems to be disconnected. 

I can't simply run sudo pppoeconf to get the internet working. If I do, it simlpy gives me a message saying that something like "it can't find the access concentrator". So I do other stuff like sudo ifconfig eth0 up, poff, pon dsl-provider. I also try killing stuff in system monitor like pppd, pdflush, etc.


After a few experiments, I do sudo pppoeconf and it can find what it needs to find. Sudo pppoeconf already has all my settings. For example, it has my username/login name from my ISP. I just have to press enter for all the questions, and enter the password that my ISP gave me.

At the final parts of the process, pppoeconf asks me:
> Your PPPD is configured now. Would you like to start the connection at boot time?                         
I answer "YES."
 
I would think that this solves it, but in reality, the connection is NOT started at boot time. What is wrong? Please help a linux-ignorant newbie.

(After the entire pppoeconf process, I have internet connection again, but it's lost after i reboot. )

Thanking you all in advance...

---

### Post by adwait on 2005-10-15
Maybe it is just that your resolv.conf is not being updated when you reboot. Try this, install resolvconf
```
sudo apt-get install resolvconf
```

Now, when your internet connection is working, copy your /etc/resolv.conf file to /etc/resolvconf/resolv.conf.f/original file.

---

### Post by hanzj on 2005-10-15
> Now, when your internet connection is working, copy your /etc/resolv.conf file to /etc/resolvconf/resolv.conf.f/original file.
adwait, i just got resolvconf installed. 

the etc/resolv.conf file has an arrow on the icon, meaning it links to a document. So do you want me to open that resolv.conf linking document and copy the contents of that and paste it into etc/resolvconf/resolv.conf.d/original file?

(I don't have a folder called resolvconf/resolv.conf.f/, but one called resolvconf/resolv.conf.d/)


If so, I must tell you that they both have the same contents:
> nameserver 210.147.240.193
nameserver 202.225.94.247

---

### Post by adwait on 2005-10-15
Yeah, I mean the same file, I made a typo :)
anyway, just insert two nameserver lines you posted here into the file.

---

### Post by hanzj on 2005-10-15
[QUOTE=adwait]Yeah, I mean the same file, I made a typo :)
anyway, just insert two nameserver lines you posted here into the file.[/QUOTE]

But it's exactly the same. If I insert those two lines from /etc/resolv.conf file to /etc/resolvconf/resolv.conf.d/original file, then  /etc/resolvconf/resolv.conf.f/original file will look like this:

> nameserver 210.147.240.193
nameserver 202.225.94.247

nameserver 210.147.240.193
nameserver 202.225.94.247

Is this what you suggest?

---

### Post by adwait on 2005-10-15
Ooh oops.......in that case just let the file remain as it is. Anyway....now try rebooting don't think you should have a problem with the net working......

---

### Post by hanzj on 2005-10-15
[QUOTE=adwait]Ooh oops.......in that case just let the file remain as it is. Anyway....now try rebooting don't think you should have a problem with the net working......[/QUOTE]

Oh, so you're saying that installing resolvconf is the solution? 

Okay, I'll reboot now. Hope everything is fine.
Thank you so much for your help adwait!!!

---

### Post by hanzj on 2005-10-15
I just rebooted. And I couldn't get automatically connected to the internet. I had to do some manual stuff. And I was wrong about what I wrote. I wrote that I just needed to do a 2-step process to get online (ifconfig eth0 up, pppoeconf), but that 2-step process didn't work. I don't know exactly how pppoeconf worked.  But what I did was just killing pppd, pdflush via system monitor. then trying various orders of poff, sudo pon dsl-provider, sudo pppoeconf, sudo ifconfig eth0 up. 

I'm not sure which order, which commands made me get online.

Is this a bug in breezy? What's keeping my ubuntu breezy from automatically initiating an internet connection at boottime?

---

### Post by adwait on 2005-10-15
Ok....once you have got the connection setup, 
```
sudo pon dsl-provider 
``` 
This is supposed to get the connection working. Or, try reconnecting
```
sudo poff
sudo pon dsl-provider

```

Once you find the one which works, just put it in a text file. Make it executable with
```
chmod +x <filename> 
```
Copy it to the /etc/init.d/ directory
Then use
```
sudo rcconf 
```
Check the box against the file you jsut created using the spacebar. This will execute that file everytime the computer starts.....so the commands that you enter manually will be automatically run. I know this is a stop gap solution.....but what the hell, as long as it works :)

---

### Post by hanzj on 2005-10-15
So strange. I rebooted after reading your last post, to see which of the two sets of commands would initiate the connection at bootup. But strangely, the connection to the internet was automatically connected.:confused: 

I'll post here in the future if it doesn't work. 

Thanks so much again, adwait, for helping me through this.

---

### Post by adwait on 2005-10-16
no problem :)

---

### Post by chiok on 2005-10-16
[http://ubuntuforums.org/showthread.php?t=75687](http://ubuntuforums.org/showthread.php?t=75687)

sudo nano /etc/network/interfaces
Comented out *iface eth0 inet static *section and add *iface eth0 inet manual *after auto eth0.

---

### Post by hanzj on 2005-10-17
Bad news: I just restarted my computer. When I got back into the desktop, the internet was not working. I tried:
```
poff
```
but:
> /usr/bin/poff: More than one pppd running and no -a option and
no arguments supplied. Nothing stopped.
So I tried ```
poff -a
```
> /usr/bin/poff: /bin/kill failed.  None stopped.
I tried ```
poff dsl-provider
```
but > /usr/bin/poff: /bin/kill failed.  None stopped.

So I went to the *System Monitor* applet and saw that there were two *ppd*s running. Under the arguments column:
> /usr/sbin/pppd call dsl-provider
and 
> call dsl-provider

It was in system monitor that I killed/ended these 2 pppd processes. 

After killing these two, I went to terminal and 
```
pon dsl-provider
```
This got the internet working again.


Some questions:
1. Where is the pattern behind this sometimes automatically-connected, sometimes not-automatically connected issue? I can't understand this.
2. why I need to know the reason why[FONT="Garamond"]the internet gets automatically connected after reboot, while other times the internet is not automatically connected[/FONT] :
so that I know how to solve this problem.
So that I can know what script to write for every bootup, if this is the solution that will be best.

---

### Post by adwait on 2005-10-17
1) I can't understand it either
2)No idea
3)Try adding these to the script
```
killall pppd
pon dsl-provider

```

---

### Post by rth on 2005-10-20
[QUOTE=chiok][http://ubuntuforums.org/showthread.php?t=75687](http://ubuntuforums.org/showthread.php?t=75687)

sudo nano /etc/network/interfaces
Comented out *iface eth0 inet static *section and add *iface eth0 inet manual *after auto eth0.[/QUOTE]

There is a way around that if you just happen to want to have a static LAN IP (like me, where I have a LAN and I want static IPs)...

Do the opposite, comment it out like so:
		# added by pppoeconf
		#auto eth0

That solved my problem with neither connection starting on boot when it was supposed to. You may also need to edit resolv.conf for DNS servers if you wish.

---

