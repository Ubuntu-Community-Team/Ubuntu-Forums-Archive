---
title: "Auto mount my other internal hard drives?"
date: 2008-06-29
forum: General Help
---

### Post by mattgaunt on 2008-06-29
Hey guys

I've hunted around trying to find out how to do this but I couldn't see how.

I want to add another 3 or 4 other ntfs hard drives so that they auto mount, I know it has something to do with my fstab but I cant remember how, or even remember having trouble with internal hard drives not auto mounting as standard.

Thanks in advance for any help

Gaunt

---

### Post by Elfy on 2008-06-29
You can use the ntfs tool to mount them, in hardy (maybe gutsy as well) one is installed by default the other not. After they are installed you canba ccess the tool in system tools I believe

```
sudo apt-get install ntfs-3g ntfs-config
```

Alternatively add them to your fstab manually, easily done I used this tutorial first time I did it, personally I prefer to do it this way

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

If you have a problem post back

---

### Post by mattgaunt on 2008-06-29
That was perfect, cheers

Gaunt

---

### Post by Elfy on 2008-06-29
You're welcome :)

---

