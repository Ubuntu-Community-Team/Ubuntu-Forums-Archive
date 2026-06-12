---
title: "How to run sudo from a shell script"
date: 2012-12-01
forum: General Help
---

### Post by Mycotheologist on 2012-12-01
I need to run chmod from a shell script but I always have to put sudo before that command. Is there a way I can get the shell script to enter the password for sudo?

---

### Post by papibe on 2012-12-01
Hi Mycotheologist.

You can use sudo in your script. The password will be asked interactively on the command line.

Another alternative would to write your code assuming it will be run as the super user (don't use sudo), and then call the script itself using sudo. For instance:
```
sudo ./myscript.sh
```
Let us know how it goes.
Regards.

---

### Post by codemaniac on 2012-12-02
+1 what papibe said.

Unix systems are designed with security as the primary point to focus on. Hence no *nix utilities will let you place password in plain text or in a script, that would defy 35 years of secure unix architecture.

---

### Post by rnerwein on 2012-12-02
> **codemaniac said:**
> +1 what papibe said.

Unix systems are designed with security as the primary point to focus on. Hence no *nix utilities will let you place password in plain text or in a script, that would defy 35 years of secure unix architecture.
you can edit the /etc/sudoers by insering to following line:

your_username ALL=NOPASSWD: /path_to/your_script/scrip_name

cheers

---

