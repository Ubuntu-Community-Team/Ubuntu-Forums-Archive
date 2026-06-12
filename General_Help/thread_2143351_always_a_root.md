---
title: "always a root"
date: 2013-05-08
forum: General Help
---

### Post by kom333 on 2013-05-08
Aiyyo! 

I've got 10.04 and when I want the root access I must type sudo su or sudo -s. I was wondering if there is a way how to always be a root. If there is a way I wanna know how to do it, please?

---

### Post by The Cog on 2013-05-08
Running all the time as root is discouraged. The way you are currently doing it is the best way.
I know it sounds like "Don't run with scissors", but there are good reasons - protection against accidents and against malware.
As you get the system set up as you like it, you will find you don't need to sudo that often anyway.

See this page:
[https://help.ubuntu.com/community/RootSudo&#8206;](https://help.ubuntu.com/community/RootSudo&#8206;)

---

### Post by monkeybrain2012 on 2013-05-08
root account is disabled by default on Ubuntu for security reasons. I find it to be desirable as there is no reason why you have to be root all the time during a session and if you log in as root anything can run. Even in other distros with root  I add myself to sudoers and use sudo to do system things on a per command basis.

I think some Windows users like to be root because they are not used to giving passwords for installing and updating etc, but this is one reason why Linux is more secure and it is easy to get used to. 

Oh, 10.04 desktop will reach end of life tomorrow, better back up your files and make a fresh install of 12.04 soon (seems like you are a LTS user)

---

