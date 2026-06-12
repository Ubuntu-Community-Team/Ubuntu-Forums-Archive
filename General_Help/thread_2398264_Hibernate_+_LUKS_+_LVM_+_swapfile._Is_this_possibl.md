---
title: "Hibernate + LUKS + LVM + swapfile. Is this possible?"
date: 2018-08-09
forum: General Help
---

### Post by Paddy Landau on 2018-08-09
I can make hibernation on a full-system encryption work with LUKS, LVM and a swap partition.
But I seem to be unable to make hibernation work with LUKS, LVM and a swap file.
Whenever I hibernate, the system closes down, but on restarting, the system ignores the hibernation file and simply does a cold boot.

Do you have any hints as to how to make Ubuntu's hibernation work with a swap file instead of a swap partition? I've looked around the 'net but found nothing that works.

Using version 18.04

---

### Post by #&amp;thj^% on 2018-08-09
Just if you don't find a suitable answer.
As a workaround, you can avoid the need to have a swap file by using LVM on top of your encrypted partition and then putting a swap partition inside of it along with your root partition, which will work fine with no special steps required.

---

### Post by Paddy Landau on 2018-08-10
Thanks, I managed to make it work with a swap partition. I was hoping for a swap file, because that's the "new, recommended" way. As I haven't been able to find an answer, I shall do as you suggest and stick with a separate partition.

---

### Post by HermanAB on 2018-08-10
Here is why:
[https://unix.stackexchange.com/questions/434177/why-a-file-as-swap-cant-be-used-for-hibernation-in-linux](https://unix.stackexchange.com/questions/434177/why-a-file-as-swap-cant-be-used-for-hibernation-in-linux)

So you can, with some effort.

---

### Post by Paddy Landau on 2018-08-10
> **HermanAB said:**
> Here is why…
That is helpful. It looks far easier, and less error-prone, to use a partition, so I'll stick with that.

Thank you

---

