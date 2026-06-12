---
title: "autostartup service"
date: 2014-04-10
forum: General Help
---

### Post by minotaur2 on 2014-04-10
Hy, I have ubuntu server 12.04.
How I can disable service from startup? With **sysv-rc-conf **I can see wich mysql it's disabled in all runlevel but it start on boot.
Only if I remove line **start on runlevel [2345]** from **/etc/init/mysql.conf**, don't start on boot.
What's correct way in Ubuntu server 12.04? Make use of **upstart** or **systemV** to manage service boot?
Thank you

---

### Post by Kirboosy on 2014-04-10
Welcome to the forums! :D

To enable mysql on boot you would run the following command
```

sudo update-rc.d mysql defaults
```

To disable mysql on boot the following command should work
```

sudo update-rc.d mysql remove
```

Hope that helps!
~Caboose

---

### Post by minotaur2 on 2014-04-14
Hy Camboose,
my request it's not only for mysql.
I want to understand how ubuntu manage service startup.
The command **update-rc.d **make only links from /etc/rc[0-6].d to /etc/init.d.
Beacause there are more different manager's startup service? What's the right on to use?
Thank you

---

### Post by Kirboosy on 2014-04-14
Ah, well that is all personal preference and it depends on who you talk to. For me I just go with whatever service manager is included by default in that distribution of Linux. If I'm on Fedora, Red Hat, CentOS I will use ckconfig since thats included with the distro by default. However when I use Ubuntu I use update-rc.d

There is no "wrong way" to Linux most of the time. Its more so finding your way that make sense to you and running with it. 

~Caboose

---

