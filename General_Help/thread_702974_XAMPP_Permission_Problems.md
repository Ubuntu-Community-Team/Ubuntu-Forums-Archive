---
title: "XAMPP Permission Problems"
date: 2008-02-20
forum: General Help
---

### Post by jjb123 on 2008-02-20
I just install the latest XAMPP and it installed fine but when I try to access localhost in my browser it says I do not have enough permissions (It is xampp saying this with an apache message). I tried chowning the htdocs folder to my group and username but it didn't work. Any ideas? Thanks.

---

### Post by enchance on 2008-02-21
> **jjb123 said:**
> I just install the latest XAMPP and it installed fine but when I try to access localhost in my browser it says I do not have enough permissions (It is xampp saying this with an apache message). I tried chowning the htdocs folder to my group and username but it didn't work. Any ideas? Thanks.
Try
```
sudo chmod -Rfv 755 htdocs
```
Although why use XAMPP if you can install LAMP directly? I installed XAMPP once but then moved to installing LAMP directly through Synaptic since it's better. It's in **Synaptic > Edit > Mark Packages by Task > LAMP Serve**r. Place all your files in /var/www/ although you could change that too (mine is in ~/www/ for convenience)

Happy phping!

---

### Post by jjb123 on 2008-02-21
Thank you, it worked!

---

