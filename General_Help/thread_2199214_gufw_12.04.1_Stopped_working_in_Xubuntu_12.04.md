---
title: "gufw 12.04.1 Stopped working in Xubuntu 12.04"
date: 2014-01-12
forum: General Help
---

### Post by mikodo on 2014-01-12
I wanted to remove one rule. So I did it. Realized I needed it to get to irc, (8001/tcp), tried to put it back and couldn't.

When I try to add a rule, it won't accept any typing in the space, to add any rules.

I tried to reset it. I deleted all rules by the resetting, and it still will not allow any new ports to be put it.

I even deleted the app (gufw), and reinstalled, still not working.

It will allow my to change Allow or Deny *all* in or out coming. (That is how I can get out to post this thread on the system to you).

I have no router, just ISP's modem hooked directly to computer.

I will have to do the ufw settings by command line, if I can I guess.

See Screenshots showing what I am talking about.

Makes me afraid I have been compromised ...

EDIT: I am going to use the CL to set my ufw rules. Makes me scare not having them. If anyone knows what might be going on with Gufw, please share. I will  leave this here, to see if anyone is having similar problems.

---

### Post by mikodo on 2014-01-12
Well, I used the CL to upload my firewall rules, with no problem. It even shows in the Gufw. But, if I delete a rule in Gufw, AGAIN, I cannot add the rule back. I had to add it by CL.

So, Gufw, is hosed for me. 

???

Thanks.

---

### Post by mikodo on 2014-01-14
Anyone have a clue, how I can fix Gufw?

---

### Post by egeezer on 2014-01-14
Never used Gufw, just ufw, but couldn't you remove Gufw via Synaptic and revert to ufw?

---

### Post by mikodo on 2014-01-14
I still like the gui, but I have to use ufw to set my rules now ...   :(

---

### Post by Dave_L on 2014-01-14
Try running gufw from the command line and see if you get any error messages:
```
gksudo gufw &
```

---

### Post by mikodo on 2014-01-14
> **Dave_L said:**
> Try running gufw from the command line and see if you get any error messages:
```
gksudo gufw &
```

Hi Dave,  

It opened Gufw. Below is what was in terminal.

 ```
gksudo gufw &
[1] 2766
mikodo@mikodo-GV465AA-ABA-a6245n:~$ 


```

---

### Post by mikodo on 2014-01-14
Time for a nap!

I'll check the thread later.

Thanks.

---

### Post by Dave_L on 2014-01-14
You could try this and look for error messages:

```
sudo grep -ir gufw /var/log
```

These are only guesses. I have no idea what's causing the problem.

---

### Post by mikodo on 2014-01-14
Thanks, Dave:

I see no errors that I understand from

```
sudo grep -ir gufw /var/log
```

---

