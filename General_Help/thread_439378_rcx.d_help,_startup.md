---
title: "rcx.d help, startup"
date: 2007-05-10
forum: General Help
---

### Post by wconstantine on 2007-05-10
The things thats listed in the /etc/rc<insert number here>.d

Is the k in front of the files meaning that they start? And the s means stop, meaning that it won't boot?

I mean I can put an s in front of the bluetooth feature for example since I don't use that, and the hplip service since I don't have any printers? And the nvidia-kernel can be terminated since I don't use Nvidia but Ati?

Is there any kind of guide that explains all the features and tells us what's necessary and whats not? 

Thanks :)

---

### Post by ohgod on 2007-05-10
I think the scripts that start with 'S' run when each runlevel is reached during bootup, while the scripts starting with 'K' run when shutting down.

Here's a guide about disabling startup/shutdown scripts that you don't need:

[http://doc.gwos.org/index.php/Speed_up_boot]("http://doc.gwos.org/index.php/Speed_up_boot")

---

### Post by wconstantine on 2007-05-10
> **ohgod said:**
> I think the scripts that start with 'S' run when each runlevel is reached during bootup, while the scripts starting with 'K' run when shutting down.

Here's a guide about disabling startup/shutdown scripts that you don't need:

[http://doc.gwos.org/index.php/Speed_up_boot]("http://doc.gwos.org/index.php/Speed_up_boot")

Exactly what I was looking for m8. Thanks alot!

---

