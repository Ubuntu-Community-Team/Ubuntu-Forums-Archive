---
title: "SSH connections hang"
date: 2008-06-24
forum: General Help
---

### Post by Tonren on 2008-06-24
I'm running OpenSSH on my Kubuntu 8.04 laptop, which is connected to the internet via a wireless g router.  It has worked error-free in the past.

After about 1 or 2 minutes of use, my SSH connection will hang.  By "hang" I mean output and input are no longer sent or received; it can happen right in the middle of drawing an application.  Sometimes it is when I'm using screen, sometimes it's not.  It appears to be somewhat connected to the amount of output being sent to the screen--it seems particularly prone to hang when I reattach a screen session on a vim file, or load irssi.

I don't think it's an issue with my ISP, because the problem happens even when I connect over the LAN.  I've been fooling around with my router's QoS settings, so that might be it, but it seems unlikely.  I've experienced intermittent lag issues with other services (port 80), but my SSH sessions are the only things consistently hanging.

Any ideas...?

---

### Post by Tonren on 2008-06-25
Bumping this... SSH is largely unusable due to this bug.  Has anyone ever encountered it before?

---

### Post by Archmage on 2008-06-25
Did you try to change the port to try if this is a port-only problem?

---

### Post by Tonren on 2008-06-25
Archmage, that was a great idea, and I tried it, but the problem has persisted.  (I did remember to forward the port through my router, etc.)

---

### Post by egosintric on 2008-06-25
2.12 - My ssh connection freezes or drops out after N minutes of inactivity.

[http://www.openssh.org/faq.html#2.12](http://www.openssh.org/faq.html#2.12)

---

### Post by Tonren on 2008-06-25
Sorry egosintric; also a potentially good idea, but this does not occur when I'm inactive.  Like I said--sometimes it will hang right in the middle of doing something.  In fact, it does seem like it hangs more often when I'm being active, switching screen tabs, writing documents in Vim, etc.

Sometimes it just lags for a few seconds and then catches up, but other times it hangs completely.

---

### Post by Archmage on 2008-06-26
Just a wild guess: It is possibile that your router/switch/hub is a little broken?

I did have this also bevor I buyed my new switch. Hanging in SSH, webpages did time out, pings don't get through the whole time, and so on.

Another idea might be, that your router can't handle that much connections. Maybe you are using also Bittorent the whole time?

Is it possibile that you could try with a different router without being connected to the internet? Just to see if the problem still exist?

---

### Post by Tonren on 2008-06-26
@Archmage: Unfortunately, I've ruled all of those out.  All of my other internet activity works fine, including web browsing, game playing and torrenting (which I turned off during my SSH testing).  I pinged my laptop from my remote server for ten minutes and it barely missed a single ping.

Though, another idea would be to forward my SSH port to a different computer on the LAN and see if the same issue was there.  I doubt it, because my local XP desktop has the same issue connecting to it, so if it is a router problem, it's happening on the LAN and WAN.

---

### Post by manfer on 2008-06-26
Why don't you first test ssh on same computer?

prompt:~$ **ssh localhost**

or

prompt:~$ **ssh local_ip**

(eg. ssh 192.168.0.5)

Same problem that way?

---

### Post by Tonren on 2008-06-26
@manfer: I'm not testing it very reliably--I'm using screen from work--but so far, the local ssh connection hasn't froze.  I obviously couldn't test whether it's lagging severely, because I can't differentiate that from lag on my remote SSH session, but it definitely hasn't frozen yet.

---

### Post by Tonren on 2008-06-27
OK... my local SSH connection is definitely not freezing at all.  What could this mean?  Remote connections are still hanging.

---

### Post by Tonren on 2008-07-03
Bumping this... this is still a serious problem for me.  It would be fantastic if someone could help.

---

### Post by vatbier on 2011-07-28
Hello there Tonren,

did you find a solution for this problem?
Because here in 2011 at my work we suffer from the same problem on a few of our virtual servers (Centos 5): the ssh connection sometimes hangs but no one of our dev people have figured out why it happens. Very frustrating.

---

### Post by Tux2 on 2011-10-15
One of my clients was having trouble with a shell that I was hosting for him and he had the exact same issue with it hanging part way into large output. By typing in
```
sudo ifconfig eth0 mtu 576
```
into the terminal it fixed the issue (of course substituting eth0 with your network device). I found that from looking at this website: [http://www.snailbook.com/faq/mtu-mismatch.auto.html](http://www.snailbook.com/faq/mtu-mismatch.auto.html)

Since this is one of the first hits on Google for it I decided to provide a solution.

---

