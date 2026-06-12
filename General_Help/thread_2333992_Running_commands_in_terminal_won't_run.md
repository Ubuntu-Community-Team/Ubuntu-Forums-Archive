---
title: "Running commands in terminal won't run"
date: 2016-08-15
forum: General Help
---

### Post by gameboy9309 on 2016-08-15
Hi, I'm running Ubuntu 16.04.1, and whenever I run a command in the terminal, it acts as if it's already ran. When I run it, it'll print out something like this:


matthew@HP-Pavilion-dv6:~$ sudo apt-get clean
matthew@HP-Pavilion-dv6:~$ 

And that's it. Really hope someone can help. Thanks

---

### Post by SeijiSensei on 2016-08-15
It doesn't reply to the terminal.  It just removes in the files under /var/apt/cache.  Do you see .debs there now that you have run the command?

---

### Post by gameboy9309 on 2016-08-15
I don't have a [COLOR=#000000]/var/apt/cache folder.[/COLOR]

---

### Post by howefield on 2016-08-15
> **gameboy9309 said:**
> I don't have a /var/apt/cache folder.

Try it the other way round...

```
/var/cache/apt/archives/
```

---

### Post by gameboy9309 on 2016-08-15
This worked, thanks. Nothing's there, so that's good. But it's just weird. Even if I run localepurge, it'll show nothing. And it used to.

---

### Post by gameboy9309 on 2016-08-15
It used to print out more stuff. Why did it stop?

---

### Post by howefield on 2016-08-16
> **gameboy9309 said:**
> It used to print out more stuff. Why did it stop?

Apt no longer keeps the downloaded .deb files, so there is nothing to "clean".

Try it for yourself.. open Files (Nautilus) and navigate to 

```
/var/cache/apt/archives
```

Open a terminal so you can still see the Files window, and install a small application eg..

```
sudo apt install cowsay
```

Watch the Files window, you'll see the cowsay packages (2 of them) appear, then when the installation is complete, you'll see them disappear/delete. Nothing to clean, so no output :)

---

