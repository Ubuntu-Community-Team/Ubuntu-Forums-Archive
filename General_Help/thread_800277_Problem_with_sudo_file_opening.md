---
title: "Problem with sudo file opening"
date: 2008-05-19
forum: General Help
---

### Post by LOLands on 2008-05-19
I have a rather stupid problem :P I needed to change the MAC adress for my NIC, but I made a stupid mistake in network interfaces file (/etc/network/interfaces). So I need to make this good again, because all networking fail to start. So I tried to open a file again from terminal (sudo gedit /etc/network/interfaces), but nothing opens :( I can open the file without root permissions, but I can`t edit the file. So what should I do? :P

Thanks!

---

### Post by strabes on 2008-05-19
Use nano. It's a terminal-based editor. Ctrl+O saves files, Ctrl+X exits.```
sudo nano /etc/network/interfaces
```

---

