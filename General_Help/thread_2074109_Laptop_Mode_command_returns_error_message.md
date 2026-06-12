---
title: "Laptop_Mode command returns error message?"
date: 2012-10-21
forum: General Help
---

### Post by HelloHAL9000 on 2012-10-21
Hey guys! :)

I installed a laptop power management utility from the Software Center. It is called Tools for Power Savings based on battery/AC status laptop-mode-tools. I am running 12.10 Quantal Quetzal on an Asus N53S alongside Windows 7.

After I installed it, the page for the utility in the Software Center said that it can be used by entering the "laptop_mode" command into Terminal. When I do so, Terminal gives me this response...

Warning: Configuration file /etc/laptop-mode/conf.d/board-specific/*.conf is not readable, skipping.
/usr/sbin/laptop_mode: 1175: /usr/sbin/laptop_mode: cannot create /var/lock/lmt-req.lock: Permission denied


I use this laptop for school, so I need some sort of battery management where I get more than 2 and a half hours (what I get right now)

What should I do? Are there other utilitize I could use where I could enter into some sort of power-saver mode?

Thanks!!!

---

### Post by 2F4U on 2012-10-21
I guess you need to use sudo in order to prevent permission problems.

---

### Post by Linuxisfast on 2012-10-21
Add Jupiter by using its ppa at [https://launchpad.net/~webupd8team/+archive/jupiter](https://launchpad.net/~webupd8team/+archive/jupiter)

Install Jupiter and it automatically tunes your system for maximum battery life.

---

### Post by HelloHAL9000 on 2012-10-22
Thanks a lot! Trying that now!

---

