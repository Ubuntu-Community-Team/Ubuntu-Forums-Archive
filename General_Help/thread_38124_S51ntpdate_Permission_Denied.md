---
title: "S51ntpdate Permission Denied"
date: 2005-05-30
forum: General Help
---

### Post by IdoMcFly on 2005-05-30
Hello !

My gf has a dual boot box winXP and Ubuntu.

She boot on windows and then Win change the clock to summer time, but since when booting Ubuntu, she got a S51ntpdate : Permission denied on clock Sync.

Any idea on how to fix this?

---

### Post by IdoMcFly on 2005-06-03
still have the problem :(

---

### Post by IdoMcFly on 2005-06-10
so nobody knows ? :'(

---

### Post by IdoMcFly on 2005-06-12
I can't find any log that can help me dto dig this problem out :?

---

### Post by desdinova on 2005-06-12
[QUOTE=IdoMcFly]I can't find any log that can help me dto dig this problem out :?[/QUOTE]
 the command

dmesg

directly after boot will give you info

try

dmesg | grep ntp

---

