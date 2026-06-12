---
title: "Disable time synch during boot"
date: 2005-08-28
forum: General Help
---

### Post by henriette_holm on 2005-08-28
Hi.
Is it possible to diable the time synch that takes place during boot? And how?

Thanks

-Henriette

---

### Post by evilghost on 2005-08-28
```

cd /etc/init.d
sudo update-rc.d -f ntpdate remove

```

---

### Post by nozey on 2005-08-28
U can do this:

```
$ sudo chmod -x /etc/init.d/ntpdate
```

Or u can download a tool that helps u add/remove scripts that start during boot. Just do it:

```
$ sudo apt-get install rcconf

To use:

$ sudo rcconf
```

EDIT: its chmod .. sorry for my mistake

---

### Post by evilghost on 2005-08-28
[QUOTE=nozey]U can do this:

```
$ sudo chown -x /etc/init.d/ntpdate
```[/QUOTE]

Wouldn't that be "chmod -x" ? ;)

I still think update-rc.d is easier.... ;)

---

### Post by nozey on 2005-08-28
uptade-rc.d is easy.
But if u want to remove more then one script, the rcconf is the easyest way.

---

### Post by henriette_holm on 2005-08-30
And the difference between this:
> ```

cd /etc/init.d
sudo update-rc.d -f ntpdate remove

```
and
> ```

$ sudo chmod -x /etc/init.d/ntpdate

```
is what? Does the first one remove it, or?

-Henriette

---

### Post by evilghost on 2005-08-30
The update-rc.d command I posted will remove it, the chmod -x command will simply make it non-executable.  Two different ways to get to the same result.  Personally, I think the update-rc.d one I posted is the way to do it.

---

