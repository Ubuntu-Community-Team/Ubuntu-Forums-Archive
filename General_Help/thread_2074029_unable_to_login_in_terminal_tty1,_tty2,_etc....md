---
title: "unable to login in terminal tty1, tty2, etc..."
date: 2012-10-20
forum: General Help
---

### Post by Mia_tech on 2012-10-20
guys, I'm unable to login from terminal tty1, tty2, etc.. I can login remotely using ssh, no problem login into x session or sudo password no problme there either, but when I switch to tty1 or 2 or 3, I can't login

help needed

Thanks

---

### Post by Toz on 2012-10-22
When you switch over to tty1, do you see anything on the screen? Are you typing in your username and password and its not getting accepted?

Does anything relevant show up in /var/log/secure when you attempt a console login?

---

### Post by mardybear on 2012-10-22
Hi Mia_tech.

I remember applying a tweak sometime ago to one of my Ubuntu systems, which disabled tty terminals 1-3 to help lean the system.

Can't remember offhand which config file was customized but i'm sure you'll find the answer in this google search link:
[http://www.google.com/search?q=ubuntu+disable+tty+1-3&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=seamonkey-a](http://www.google.com/search?q=ubuntu+disable+tty+1-3&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=seamonkey-a)

Do you still have tty4-6? If so, you may have applied a similar 'tweak' previously that you forgot about?

mardybear

---

### Post by Mia_tech on 2012-10-22
> **Toz said:**
> When you switch over to tty1, do you see anything on the screen? Are you typing in your username and password and its not getting accepted?

Does anything relevant show up in /var/log/secure when you attempt a console login?

yeah, I'm getting authentication failure in the logs... but I'm able to login to my X session, and sudo password works too
```

Oct 22 18:36:08 computer1 login[1216]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=john
Oct 22 18:36:10 computer1 login[1216]: FAILED LOGIN (1) on '/dev/tty1' FOR 'john', Authentication failure
Oct 22 18:36:22 computer1 login[1216]: FAILED LOGIN (2) on '/dev/tty1' FOR 'john', Authentication failure
```

---

### Post by Mia_tech on 2012-10-22
> **mardybear said:**
> Hi Mia_tech.

I remember applying a tweak sometime ago to one of my Ubuntu systems, which disabled tty terminals 1-3 to help lean the system.

Can't remember offhand which config file was customized but i'm sure you'll find the answer in this google search link:
[http://www.google.com/search?q=ubuntu+disable+tty+1-3&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=seamonkey-a](http://www.google.com/search?q=ubuntu+disable+tty+1-3&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:unofficial&client=seamonkey-a)

Do you still have tty4-6? If so, you may have applied a similar 'tweak' previously that you forgot about?

mardybear

I've tried different tty1...6 with same results

---

### Post by Toz on 2012-10-22
> **Mia_tech said:**
> yeah, I'm getting authentication failure in the logs... but I'm able to login to my X session, and sudo password works too
```

Oct 22 18:36:08 computer1 login[1216]: pam_unix(login:auth): authentication failure; logname=LOGIN uid=0 euid=0 tty=/dev/tty1 ruser= rhost=  user=john
Oct 22 18:36:10 computer1 login[1216]: FAILED LOGIN (1) on '/dev/tty1' FOR 'john', Authentication failure
Oct 22 18:36:22 computer1 login[1216]: FAILED LOGIN (2) on '/dev/tty1' FOR 'john', Authentication failure
```

Hmmm, looks like a wrong password error. 
Have you made any changes to your /etc/security/access.conf file? Can you post the contents?

Have you performed any system hardening activities on this computer?

---

### Post by Mia_tech on 2012-10-23
> **Toz said:**
> Hmmm, looks like a wrong password error. 
Have you made any changes to your /etc/security/access.conf file? Can you post the contents?

Have you performed any system hardening activities on this computer?

nope, but the whole file is commented out...

---

