---
title: "Checkgmail with gmail 2.0"
date: 2007-11-01
forum: General Help
---

### Post by Curtisc on 2007-11-01
Anyone else having problems with checkgmail after the recent updates to gmail?

The first time checkgmail is run, I am notified of new mail.  However, after that it constantly says "checking gmail".  The new emails that I was notified about are not marked as read (even if I click "mark as read"), and further new emails are not detected.  I can quit the program and re-run it, and the first time it checks all is well.

This happens on two computers, so I think it has something to do with the new gmail, but I thought I'd check if anyone else has this problem.

---

### Post by kshane on 2007-11-01
> **Curtisc said:**
> Anyone else having problems with checkgmail after the recent updates to gmail?

The first time checkgmail is run, I am notified of new mail.  However, after that it constantly says "checking gmail".  The new emails that I was notified about are not marked as read (even if I click "mark as read"), and further new emails are not detected.  I can quit the program and re-run it, and the first time it checks all is well.

This happens on two computers, so I think it has something to do with the new gmail, but I thought I'd check if anyone else has this problem.

Is this a client or the web-based version?  I just set up a new account on Gmail , but I use Thunderbird as a client and I have no issues.

Kevin

---

### Post by Sim777 on 2007-11-01
I opened gmail in firefox and I don't see any problems.

---

### Post by Curtisc on 2007-11-01
This is specific to the "checkgmail" program (the perl based one with the red icon, not "gmail-notify" with the blue icon).  Gmail itself is working fine.

---

### Post by akShane on 2007-11-02
This bug was posted on Checkgmail's Sourceforge bug tracker on 10/30 (#1822792).  We'll just have to wait for the developer to bring the code in line with Gmail's new version.  That's my favorite feature, too...

---

### Post by vgrisham on 2007-11-06
Bummer. I love checkgmail. It's such a time saver to just zap messages from the drop down menu rather than have to pull up the browser. I think I'll contribute some dough at [http://checkgmail.sf.net](http://checkgmail.sf.net).

On the upside for me, I had just switched to 64-bit Gutsy and was blaming the architecture. I'm glad it's a universal woe. The greasemonkey gmail script was left behind as well.

---

### Post by jasonland on 2007-11-06
Yep I'm having the same problem. Hope they fix it soon...

---

### Post by czmiel on 2007-11-07
quick workaround (the latest SVN version):
```

sudo aptitude install checkgmail
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

```
Regards

---

### Post by bawilson2 on 2007-11-07
> **czmiel said:**
> quick workaround (the latest SVN version):
```

sudo aptitude install checkgmail
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

```
Regards

I tested this out and it works great.  Thanks!

---

### Post by fragos on 2007-11-07
I'd check out cgmail, it's my favorite.  I just like the way it works.

---

### Post by vgrisham on 2007-11-07
> **czmiel said:**
> quick workaround (the latest SVN version):
```

sudo aptitude install checkgmail
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

```Regards

Thank you! That worked well, though I had to uninstall first.

---

### Post by suupaabaka on 2007-11-08
Only thing is "compose mail" opens up Gmail proper, rather than just fields for an email... oh well. I hope the creator is able to fix it. It's easily the handiest non-essential piece of software on my PC, I think. 

Beats all the other Gmail checkers hands down... even the official one! :D

---

### Post by bucik85 on 2007-11-09
Thanks. Dzi&#281;ki. :)

---

### Post by hotweiss on 2007-11-09
That worked, THANKS. CHECK GMAIL IS SO CONVENIENT.

---

### Post by mustang on 2007-11-12
> **czmiel said:**
> quick workaround (the latest SVN version):
```

sudo aptitude install checkgmail
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

```
Regards

Thank you sir!

---

### Post by midtown on 2007-11-14
> **czmiel said:**
> quick workaround (the latest SVN version):
```

sudo aptitude install checkgmail
wget http://checkgmail.svn.sourceforge.net/viewvc/*checkout*/checkgmail/checkgmail
sudo mv checkgmail /usr/bin/
sudo chmod +x /usr/bin/checkgmail

```
Regards

Thanks this worked, so wonderful! :popcorn:

---

### Post by Takahani on 2007-11-15
It worked also here !
But I still have the locale problem, displaying french accent isn't working fine on x64 processor
Anyone has find a solution ?

---

