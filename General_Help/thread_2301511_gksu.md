---
title: "gksu"
date: 2015-11-02
forum: General Help
---

### Post by mikodo on 2015-11-02
Hello everyone.

I just want to know, if [this]("https://help.ubuntu.com/community/RootSudo") is still the appropriate documentation. 

Even though I had to run an install command to get gksu on 14.04 functional. I believe it "ain't broke". 

Why?  For me ... KISS.

Thank you.

---

### Post by kryten35 on 2015-11-02
Yes.But i dont know why you installed gksu.

Ubuntu uses sudo/gksudo  and these are installed by default.

Edit :sorry gksudo is not installed by default

---

### Post by grahammechanical on 2015-11-02
I heard that gksudo/gksu is now deprecated. In fact at one point during the 15.10 development period gksu could not be installed. It was not in the repositories. So, I am surprised that you were able to install it. Apparently, somebody changed their minds.

I am now in the habit of using

```
sudo - H nautilus
sudo -H gedit
```

I do believe that documentation is still the appropriate documentation to link to if someone wants to know how to enable the root account. 

>  **-H, [B]--set-home**[/B]
**[B] Request that the security policy set the HOME  environment variable to the home directory specified by the target  user's password database entry. Depending on the policy, this may be the  default behavior.**[/B]


[http://www.sudo.ws/man/1.8.14/sudo.man.html](http://www.sudo.ws/man/1.8.14/sudo.man.html)

Regards.

---

### Post by mikodo on 2015-11-03
Thank you, Graham.

It was the thread that ?you started on pkexec that, I was reading tonight that got me questioning about it. With 14.04 repos, gksu is still available. 

I'll read the page in the link you showed us. I didn't catch that, if you mentioned it before.  I prefer not to use sudo -i with Thunar. It was until you responded, to be my replacement to gksu though, if needed. It's good to know that you think, sudo -H is a safe alternative. 

I stopped trying with pkexec as, I don't know if one should.

Regards.

---

