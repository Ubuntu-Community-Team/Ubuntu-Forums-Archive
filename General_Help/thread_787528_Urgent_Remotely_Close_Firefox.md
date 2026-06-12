---
title: "Urgent: Remotely Close Firefox"
date: 2008-05-09
forum: General Help
---

### Post by jabagawee on 2008-05-09
Alright guys, I have a huge problem. I'm a high school student with a giant computer addiction. It seems that most of my wasted time (aka 99%) is spent running Mozilla Firefox. I want a way to remotely shut down Firefox from any computer on the web. My main purpose: give my trusted friend permission to kill Firefox at will, mainly when I tell her that I'm procrastinating with my homework. Is there way to do so? I was thinking along the lines of checking an inbox for a specific message, or running a webserver with a chunk of code to run "killall firefox-bin" on my box. My idea came a LifeHacker post at: [Shutdown Windows With a Text Message]("http://lifehacker.com/software/remote-computing/shutdown-windows-with-a-text-message-172873.php"). Speed is of the essence, because the sooner I set this up, the sooner I can do better in school (aka, actually get to doing homework).

---

### Post by sekinto on 2008-05-09
Why don't you just learn to fight your procrastanation. If you are a true procrastonator, even if your friend kills Firefox, you will still find something else to do.

---

### Post by jabagawee on 2008-05-09
I know that that's the true way to stop my problem. But hey, let's just "hypothetically" say it's under different circumstances. I'm not on these forums for moral advice; I want techie answers! :P

And no, I really don't have much to do other than Firefox. Other than that, it's Pidgin, but I'm usually talking with my super-trusted friend who would just force me to do homework anyways. XD

---

### Post by asrai on 2008-05-09
I can't assist with your question (I'm not that smart!) but this firefox extension may help: [http://getmeetimer.com/index.htm](http://getmeetimer.com/index.htm)  

Good luck with the school work! I understand because I did the same myself (although it was netscape in those days!)

---

### Post by jabagawee on 2008-05-09
Tried it. The problem with the extension is that I have the power to override it. I understand that with root privileges, I could easily circumvent my own methods of keeping me out. However, I know that giving my friend the off button will be so much more effective.

---

### Post by jabagawee on 2008-05-09
Hoping that more people will sign on in the morning. bump~

---

### Post by Monicker on 2008-05-09
Use the power of sudo:

```
sudo visudo
```

add this line at the bottom

```
username     ALL = /usr/bin/killall firefox-bin
```


Then username can do

```
sudo killall firefox-bin
```



*EDIT: The above presumes that username has ssh access, as mentioned in the post following mine.   :)*

---

### Post by -grubby on 2008-05-09
You can try using SSH. Here's a guide on it : [https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

---

### Post by Joeb454 on 2008-05-09
> **sekinto said:**
> Why don't you just learn to fight your procrastanation. If you are a true procrastonator, even if your friend kills Firefox, you will still find something else to do.

You mean like? Open firefox again?

---

### Post by mrsteveman1 on 2008-05-09
If you can disable a firefox extension as root you can do anything on the box, including reverse whatever it is you end up implementing :D

Perhaps you need to not set a root password and remove your user from sudo, that way you have to boot in single user to undo something.

An idea i have would be to use port knocking, setup your machine so that when a specific sequence of ports is hit remotely, your box kills firefox. This isn't insecure like allowing someone to run scripts remotely, but still effective and easy to do.

Of course this requires that your firewall either participate in the port knocking or let the traffic through, otherwise it won't work.

You could also setup another user account that can execute single commands remotely but nothing else, i think you can do that with ssh and some of the available shells.

---

### Post by jabagawee on 2008-05-09
> **Monicker said:**
> Use the power of sudo:

```
sudo visudo
```

add this line at the bottom

```
username     ALL = /usr/bin/killall firefox-bin
```


Then username can do

```
sudo killall firefox-bin
```



*EDIT: The above presumes that username has ssh access, as mentioned in the post following mine.   :)*
Well, true, but at least it'll shock me into doing my homework a little. :P

Also, my friend is totally computer-inept and uses Windows. Is there a way I could write a batch script for her so she can simply double click it? I could use a dynamic DNS service to be accessible at all times, then the batch script would run PuTTY with parameters telling it to "sudo killall firefox-bin". Please clarify your post a bit; let's theorize I have an account called *joeschmittyquiqui*. The line I would add to visudo would be: 
```
joeschmittyquiqui     ALL = /usr/bin/killall firefox-bin
```

Am I correct?

---

### Post by Monicker on 2008-05-09
Yes.


As for putty, you can use the plink tool they provide for batch stuff:

[http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter7.html#7.3]("http://the.earth.li/~sgtatham/putty/0.53b/htmldoc/Chapter7.html#7.3")


She will still need to be competent enough to enter her password when prompted.  :P  She would have to enter it twice, once for authentication and once for the actual sudo command, unless you change the entry to

```
username     ALL = NOPASSWD: /usr/bin/killall firefox-bin
```

---

### Post by vdawg on 2008-05-09
This is an interesting idea, I wanted to implement something like this for a whole different reason, I had some questions tho..

A) how do you set it up :p

B) suppose someone were to portscan you, would the ports get "knocked"?

thanks!

> **mrsteveman1 said:**
> If you can disable a firefox extension as root you can do anything on the box, including reverse whatever it is you end up implementing :D

Perhaps you need to not set a root password and remove your user from sudo, that way you have to boot in single user to undo something.

An idea i have would be to use port knocking, setup your machine so that when a specific sequence of ports is hit remotely, your box kills firefox. This isn't insecure like allowing someone to run scripts remotely, but still effective and easy to do.

Of course this requires that your firewall either participate in the port knocking or let the traffic through, otherwise it won't work.

You could also setup another user account that can execute single commands remotely but nothing else, i think you can do that with ssh and some of the available shells.

---

### Post by Monicker on 2008-05-09
> **vdawg said:**
> This is an interesting idea, I wanted to implement something like this for a whole different reason, I had some questions tho..

A) how do you set it up :p

B) suppose someone were to portscan you, would the ports get "knocked"?

thanks!

B) Once I was able to bypass port knocking on one of our servers at work, by using a particular port scanner which is extremely fast.  It may have just been our implementation - using iptables rules.  We never tried the daemons which run specifically to handle port knocking.

---

### Post by vdawg on 2008-05-09
> **Monicker said:**
> B) Once I was able to bypass port knocking on one of our servers at work, by using a particular port scanner which is extremely fast.  It may have just been our implementation - using iptables rules.  We never tried the daemons which run specifically to handle port knocking.

Hmm, I wouldn't say that it is a safe idea then :p

---

### Post by jabagawee on 2008-05-09
Alrighty, let's just forget about SSH for a second here. Is there a simpler way, whether it be port knocking or anything else? Elaborate on it too! Tell us what port knocking is!

---

### Post by jabagawee on 2008-05-09
-read what port knocking is-

God, I'm sorry I asked. Maybe I should run an Apache server with a clicky button to run a script on my box. With a password and stuff. Would that be easier?

---

### Post by mrsteveman1 on 2008-05-12
Port knocking isn't insecure at all. It's highly unlikely that someone would be able to hit say, 10 different random ports, in order, in less than a minute anyway.

If your firewall allows people to port scan that fast thats the security hole, you should be blocking port scans, and a lot of firewalls will do this for you quite easily.

---

