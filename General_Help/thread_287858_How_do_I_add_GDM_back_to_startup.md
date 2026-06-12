---
title: "How do I add GDM back to startup?"
date: 2006-10-29
forum: General Help
---

### Post by paul6 on 2006-10-29
Following another posters advice, I used the command "sudo update-rc.d -f gdm remove" to remove GDM from startup so I could boot straight into the terminal.

Well now I want to reverse this and go back to GDM. The command he gave me does not seem to work. 

```
paul@ubuntu:~$ sudo update-rc.d gdm start 20 2 3 4 5
update-rc.d: error: expected runlevel [0-9S] (did you forget "." ?)
usage: update-rc.d [-n] [-f] <basename> remove
       update-rc.d [-n] <basename> defaults [NN | sNN kNN]
       update-rc.d [-n] <basename> start|stop NN runlvl [runlvl] [...] .
                -n: not really
                -f: force
paul@ubuntu:~$

```

How can I fix it?

---

### Post by jocko on 2006-10-29
I'm not sure what the proper way is, but you should be able to do it like this:
```
sudo ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc3.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc4.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc5.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc0.d/K01gdm
sudo ln -s /etc/init.d/gdm /etc/rc1.d/K01gdm
sudo ln -s /etc/init.d/gdm /etc/rc6.d/K01gdm
```

---

### Post by paul6 on 2006-10-29
> **jocko said:**
> I'm not sure what the proper way is, but you should be able to do it like this:
```
sudo ln -s /etc/init.d/gdm /etc/rc2.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc3.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc4.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc5.d/S13gdm
sudo ln -s /etc/init.d/gdm /etc/rc0.d/K01gdm
sudo ln -s /etc/init.d/gdm /etc/rc1.d/K01gdm
sudo ln -s /etc/init.d/gdm /etc/rc6.d/K01gdm
```

Worked, thanks!

---

