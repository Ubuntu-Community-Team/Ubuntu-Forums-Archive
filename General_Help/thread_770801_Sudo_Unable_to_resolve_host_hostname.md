---
title: "Sudo: Unable to resolve host: hostname"
date: 2008-04-27
forum: General Help
---

### Post by leech38128 on 2008-04-27
I don't know if this has been talked about yet, since I could not find it anywhere in the forums...
I cannot seem to use 'sudo <command>' without getting 'sudo:unable to resolve host: *hostname*. 
```
leech@stephanie:~/Templates$ sudo ./configure
sudo: unable to resolve host stephanie 
```


 I have even tried to use this command as the root user to no avail. I am running Hardy x32 NOT from an upgrade.  I don't have anything non-standard install besides AWN and Screenlets, which I installed through 'Synaptic'. 
Any help on this would be graciously accepted.

---

### Post by Monicker on 2008-04-27
I ran into this problem yesterday, after playing around with Samba. Samba had modified the entry in /etc/hosts for my machine.

Go to System -> Administration -> Network -> Hosts

Check the entry for 127.0.1.1 and see if it matches the hostname of stephanie.  If not, change it back to stephanie.

---

### Post by Ayzen on 2008-04-27
I had the same problem. The Monicker's solution has solved it. Thanks. :)

---

### Post by ublackwhiteu on 2008-08-17
> **Monicker said:**
> I ran into this problem yesterday, after playing around with Samba. Samba had modified the entry in /etc/hosts for my machine.

Go to System -> Administration -> Network -> Hosts

Check the entry for 127.0.1.1 and see if it matches the hostname of stephanie.  If not, change it back to stephanie.

oh my, thanks so much. I was searching the net for two hours now until I found this post. now everything works as it should.

karma + for you Monicker :D


Edit: I can't find the Thanks option, where is it hidden?

---

### Post by michael_1234 on 2008-08-21
> **ublackwhiteu said:**
> oh my, thanks so much. [...] karma + for you Monicker :D
Edit: I can't find the Thanks option, where is it hidden?

...Yeah, I was wondering the same thing!! Especially, since YOUR post has the "thanks" icon (lower right, a little yellow star + blue badge, next to "quote"/"reply") -- and the other posts do not..!?  

Then, I found this in one of the forum how-to's:  "[All about the Thanks feature]("http://ubuntuforums.org/showthread.php?t=702596")":[INDENT]*"A few notes:*
** The Thanks feature doesn't show up on posts that were in existance before it was implemented.*
* * The option to remove the Thanks shows up after you Thank someone.*
* * Not all forums have this feature.*
* * The ability to thank  a post **seems to disappear after 60 days.***"
[/INDENT]cheers,
-m

---

### Post by iamsolo on 2009-08-07
i am using a vps and it comes up with this can you help me please

---

### Post by syamsajja@ubu on 2009-10-15
HI still the same problem in /etc/hosts it is same please help me

---

### Post by syamsajja@ubu on 2009-10-15
hi still same problem /etc/hosts is right can you help me

---

### Post by TunaCanTommy on 2009-10-15
I'm running Karmic on an ASUS EeePC and I had a similar problem and solved it by doing the following:

I originally had a hostname of - ASUS EeePC

I think the space between the word was the problem. I looked at all the files related to hostname:

```
cat /etc/hosts
```

```
cat /etc/hostname
```

```
hostname --long
```

And they all had the same hostname 'ASUS EeePC' . . . so I decided to make a change and see what happened.

I edited the file /etc/hosts and /etc/hostname and changed each to just - 'EeePC' (w/o the quotes) _without any spaces_.

I rebooted and everything was working fine . . . other parts of the files got updated/modified to add the 'localhost' and 'local-domain' elements discussed in this thread and in others.  And no more sudo error messages.

---

### Post by IkeLewis on 2010-12-06
Worked perfectly for me... kudos TunaCanTommy

---

### Post by ben2talk on 2011-03-20
> **Monicker said:**
> I ran into this problem yesterday, after playing around with Samba. Samba had modified the entry in /etc/hosts for my machine.

Go to System -> Administration -> Network -> Hosts

Check the entry for 127.0.1.1 and see if it matches the hostname of stephanie.  If not, change it back to stephanie.

Menu entry 'System -> Administration -> Network'
This does not exist on my Maverick menu ! ! !

---

### Post by 5149.5 on 2011-03-20
> **ben2talk said:**
> Menu entry 'System -> Administration -> Network'
This does not exist on my Maverick menu ! ! !

You can find the hosts file in /etc. It's called hosts. :D

---

### Post by RedOctober17 on 2011-09-14
I've got Ubuntu 11.04 on an Acer AspireOne, and this does **not** resolve the issue. I have gone into the Hosts file and changed it to match the computer's network name, but sudo still fails to resolve the host name.

---

