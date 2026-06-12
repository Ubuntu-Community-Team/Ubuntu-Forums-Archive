---
title: "Permission error in bind9"
date: 2023-01-17
forum: General Help
---

### Post by carlosgamer98yt on 2023-01-17
[COLOR=#232629][FONT=-apple-system]When I download bind9 I stop it and run it to see if it works. There are no problems, but when I start modifying the files to configure it and I'm done, I get a permissions denied error. Here is the file with all the config: [/FONT][/COLOR][https://bit.ly/3XD8HBH](https://bit.ly/3XD8HBH)[COLOR=#232629][FONT=-apple-system] (I need to say that I tried with other Ubuntu flavors (Ubuntu server, desktop, Kubuntu, Xubuntu) and it says the same thing. I tried to give all the permissions and file ownership to bind9, but it always says the same thing, permissions denied). I'm using the latest version of Ubuntu Server 22.04 in a VM on VirtualBox. Here is its log file: [/FONT][/COLOR][https://bit.ly/3CSmJaA](https://bit.ly/3CSmJaA)[COLOR=#232629][FONT=-apple-system] .[/FONT][/COLOR]

---

### Post by ActionParsnip on 2023-01-17
Did you run the text editor using sudo or is this the service not being able to read the config files?

---

### Post by carlosgamer98yt on 2023-01-17
well I used sudo to make the config (using sudo nano) and when I do sudo service bind9 restart it when the error appear (all the files are ok)

---

### Post by SeijiSensei on 2023-01-17
The "bind" user needs to own the contents of /etc/bind. The directory /var/bind is owned by root:bind with both having write privileges.

```
drwxrwxr-x  2 root         bind         4096 Aug 28 18:23 bind
```

Try "cd /etc; sudo chown bind:bind -R bind". That will make the owner and group "bind" for all files and subdirectories in /etc/bind.

---

### Post by carlosgamer98yt on 2023-01-17
I already did it, and its says the same. I think that it has to be some configuration file, named.conf.local or named.conf.options? I think that I will make another ubuntu server vm and reinstall it and look carefully and compare and try things, buts its rare that executing named-checkconf doesn't show any error (I know that if not showing anything after executing the command its means that every config file is fine).

---

### Post by carlosgamer98yt on 2023-01-17
I already know what is the problem, somehow in the named.conf.options the line of "directory "/var/cache/bind";" is deleted and that why the permission error

---

### Post by SeijiSensei on 2023-01-17
It should have bind:bind ownership and write permissions for the bind user.

---

