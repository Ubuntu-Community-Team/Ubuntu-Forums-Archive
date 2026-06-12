---
title: "Ubuntu w/o username and passwd"
date: 2007-04-02
forum: General Help
---

### Post by SNYP40A1 on 2007-04-02
Is there a way that I can not have to type my username and password everytime I log on?  And just leave the username and password for root activities.  I am sharing the computer and I would like to allow others to use it as well without having to create separate accounts.  (Yes, I trust the people that I live with)

---

### Post by spin2cool on 2007-04-02
How to automatically log in:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_automatic_login_into_GNOME_.28not_secure.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_automatic_login_into_GNOME_.28not_secure.29)

Running as root all the time is a **bad idea**.  It's not just a matter of trusting the people that you live it.  I'd be more concerned about exploits and vulnerabilites that may take advantage of you running as root.  By doing so, you're throwing away much of the security advantage that you gain by running linux.

If you fully understand the risks and still really want to do it, I believe the ubuntu guide linked above has instructions on how to run as root.

---

### Post by spin2cool on 2007-04-02
Ahhh - i misunderstood your post, sorry.  Yes, it's good to leave a username/pass for root activities.  Sorry for the lecture :oops: :)

---

### Post by Titus A Duxass on 2007-04-02
Just edit your gdm.conf file or the kde equivalent to enable autologin.

I think it's in /etc/GDM/

---

### Post by aysiu on 2007-04-02
> **Titus A Duxass said:**
> Just edit your gdm.conf file or the kde equivalent to enable autologin.

I think it's in /etc/GDM/
Or Alt-F2 ```
gksudo gdmsetup
``` or System > Administration > Login Window

---

### Post by SNYP40A1 on 2007-04-02
> **spin2cool said:**
> Ahhh - i misunderstood your post, sorry.  Yes, it's good to leave a username/pass for root activities.  Sorry for the lecture :oops: :)

No problem, it was a good point to make.  I agree that it is good to leave password protection for root activities.

---

