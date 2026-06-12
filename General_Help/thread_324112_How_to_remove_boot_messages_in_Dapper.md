---
title: "How to remove boot messages in Dapper"
date: 2006-12-23
forum: General Help
---

### Post by larini on 2006-12-23
Hi, there is a way to remove that messages during boot in Dapper? Just like Edgy?

Thanks.

---

### Post by Quite Interesting on 2006-12-23
Well doing the reverse of this adds boot messages in edgy so this should work.

```

sudo gedit /boot/grub/menu.lst

```

Then find the entry you use to boot up. You can work this out by looking at the number next to default, then going to the menu entries and start counting from zero until you get to the number next to default. Finally add quiet in between ro and splash so that your entry looks something like this.

```

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-26-386 root=UUID=8d36a2b7-e2c4-47f4-9bde-c35ab0674edc ro quiet splash ide=nodma linux=nolapic noapic
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

```

Of course it won't look exactly like that but it gives you an idea where to put the quiet.

Hope that helps

---

