---
title: "laptop mode tools not enable correcly"
date: 2014-06-03
forum: General Help
---

### Post by xavierNC on 2014-06-03
Hello

I am using laptop-mode-tools with ubuntu 14.04 on a dell vostro 3460.

when plugged:

cat /proc/sys/vm/laptop_mode give 0 . all good!

when i unplugged (computer already ON):

cat /proc/sys/vm/laptop_mode give 2 . all good. powertop showwing all items as [good].

Now, if i start the computer on battery

cat /proc/sys/vm/laptop_mode give 5, and powertop is not happy at all, neither is the autonomy.

If i do: /etc/init.d/laptop-mode restart

cat /proc/sys/vm/laptop_mode give 2 and all is back to normal.

Does anyone know whats wrong with my configuration and why do i get in mode 5 when i start teh computer on battery ? how can i force it to start in mode 2 .

Thanks

Xavier

---

