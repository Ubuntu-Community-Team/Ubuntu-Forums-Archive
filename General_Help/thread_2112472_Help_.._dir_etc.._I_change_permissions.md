---
title: "Help .. dir etc.. I change permissions"
date: 2013-02-04
forum: General Help
---

### Post by ThePinkPanther on 2013-02-04
I change permissions the dir /etc , i can't execute sudo ...

sudo output :

```
sudo: /etc/sudoers es escribible por todos
sudo: no se encontraron fuentes sudoers válidas, saliendo
sudo: no se puede inicializar la política de plugin
```As I can restore the folder with the correct permissions etc?

sorry for my bad English, I speak Spanish.

---

### Post by dan000 on 2013-02-04
I'd recommend you reboot your computer into recovery mode (or use a LiveCD), and manually change the permissions. /etc/sudoers, by the way should be 440, owned by root:root.

I had to do this once, not because my permissions got messed up, but because my sudoers file got messed up by a poorly written post-install script.

And, by the way, it's a bad idea to change the permissions on all of etc. The files in there, for the most part, have sensible permissions to begin with. Unless you're certain you know what you're doing, you shouldn't ever need to change permissions on anything within /etc, and then, you should only do it to individual files, not everything.

---

### Post by ThePinkPanther on 2013-02-04
> **dan000 said:**
> I'd recommend you reboot your computer into recovery mode (or use a LiveCD), and manually change the permissions. /etc/sudoers, by the way should be 440, owned by root:root.

I had to do this once, not because my permissions got messed up, but because my sudoers file got messed up by a poorly written post-install script.

And, by the way, it's a bad idea to change the permissions on all of etc. The files in there, for the most part, have sensible permissions to begin with. Unless you're certain you know what you're doing, you shouldn't ever need to change permissions on anything within /etc, and then, you should only do it to individual files, not everything.


thanks in recovery mode then the command would be next? , Chmod 440 / etc?

---

### Post by dan000 on 2013-02-04
> **ThePinkPanther said:**
> thanks in recovery mode then the command would be next? , Chmod 440 / etc?

To fix sudoers specifically, do 
```

chmod 440 /etc/sudoers
chown root:root /etc/sudoers # this part probably isn't necessary, but it can't hurt

```

Once sudoers is fixed, you can boot back into your system and use sudo again. If you still have other things that need to be fixed, you can do those with sudo later on.

---

### Post by ThePinkPanther on 2013-02-04
> **dan000 said:**
> To fix sudoers specifically, do 
```

chmod 440 /etc/sudoers
chown root:root /etc/sudoers # this part probably isn't necessary, but it can't hurt

```Once sudoers is fixed, you can boot back into your system and use sudo again. If you still have other things that need to be fixed, you can do those with sudo later on.
because it will help me a lot. I love you

---

