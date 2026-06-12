---
title: "Booting into Ubuntu via Windows?"
date: 2006-12-25
forum: General Help
---

### Post by robcarr2 on 2006-12-25
Hello,

I was wondering if there is anyway of booting into Ubuntu via Windows. It is pretty important I keep my current MBR but I miss Ubuntu :(

I have tried using VMWare and running Ubuntu in a Virtual Machine but it seems to be very choppy.

Is there anyway at all of booting into Ubuntu without having GRUB installed, as I said I really need to keep my current MBR.

Thanks, Rob

---

### Post by Vox754 on 2006-12-25
Seems odd to me.

You could try searching in the forums
[http://ubuntuforums.org/tags/](http://ubuntuforums.org/tags/)

---

### Post by jjross on 2006-12-25
You could install grub to a cd or a floppy and boot from that,
look around on the forum, there is a How To somewhere to do this

---

### Post by bodhi.zazen on 2006-12-25
> **robcarr2 said:**
> I was wondering if there is anyway of booting into Ubuntu via Windows. It is pretty important I keep my current MBR but I miss Ubuntu :( 

Why ? I do not see how gurb in your MBR would be problematic in the least .....

> I have tried using VMWare and running Ubuntu in a Virtual Machine but it seems to be very choppy.

Yes, well VMWare is the "start of the art".

> Is there anyway at all of booting into Ubuntu without having GRUB installed, as I said I really need to keep my current MBR.

Thanks, Rob

Again, just install grub into your MBR.

If you prefer You can boot from a floppy.

See here:

SuperGRUB: [http://adrian15.raulete.net/grub/tiki-index.php](http://adrian15.raulete.net/grub/tiki-index.php)

To set up yourself:

Boot the ubuntu Live CD

In a terminal:

```
s;udo grub
```

This will bring the grub prompt.

Type:```
Find /boot/grub/stage1
```

This will identify your Ubuntu partition in grub speak [quote] (Hdx,y)

Now, at the grub prompt, insert a formatted floppy,

```
root (hdx,y)
setup fd0
quit
```

---

### Post by robcarr2 on 2006-12-27
I dont want it in my MBR as I have a Dell computer and there is a thing called the Dell System Restore utility which can restore the state of my first partition to before it was booted up for the first time which is very handy when wanting to start fresh on Windows as I dont have to install any drivers, or do any formatting, it does it all within 20 minutes time.

I am working with Linux on my laptop now instead of my computer anyway, thanks for all the replies though :)

---

