---
title: "Type accented characters in linux console"
date: 2007-08-07
forum: General Help
---

### Post by sistoviejo on 2007-08-07
Hello,
I have an english layout keyboard but need to type accented characters in the linux console. So far I have only seen methods for x-windows.
In windows I would use Alt+164 for an "ñ"... Alt+162 for an "ó"... etc. I haven't found the way to do it in Linux CLI. Is there a simple way to do it like there is in windows?
Thanks in advance!! :)

---

### Post by milosz.galazka on 2007-08-07
Try searching in */etc/console-tools/* and */etc/console-setup/*.

---

### Post by sistoviejo on 2007-08-08
thanks for the reply.
what should I look for there?
will this work in other distros?

---

### Post by shirilover on 2007-08-08
You may want to look at using the 'Compose key' to input accented characters.

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

---

### Post by sistoviejo on 2007-08-08
> **shirilover said:**
> You may want to look at using the 'Compose key' to input accented characters.

[https://help.ubuntu.com/community/ComposeKey](https://help.ubuntu.com/community/ComposeKey)

Sorry I can't use that because I don't use gnome nor X-windows. 
Thanks for the reply though.

---

### Post by nitro_n2o on 2007-08-08
well I don't have a directed answer but i recommend you reading this: [http://linux.about.com/od/ttl_howto/a/hwtttl09t05.htm](http://linux.about.com/od/ttl_howto/a/hwtttl09t05.htm) a lot of info out there and many links

---

### Post by sistoviejo on 2007-11-02
Here's a solution that works for US layout keyboards on any flavor of Linux and also Windows XP.

Install the "United States International" keyboard layout.
You might find it by other names... "US-intl", "English-intl" etc.

After installing and enabling this layout these keys will become dead keys: [SIZE="5"]~ " ` '[/SIZE] 

This means you will have to press space key after pressing one of them for the usual effect. 

If you want to make an [SIZE="5"]á[/SIZE] character you have to press the [SIZE="5"]'[/SIZE] (apostrophe) key and afterwards press the [SIZE="5"]a[/SIZE]  key.

There are many other combinations... For example:

[SIZE="5"]~[/SIZE]  + [SIZE="5"]n[/SIZE] will make [SIZE="5"]ñ[/SIZE]

---

