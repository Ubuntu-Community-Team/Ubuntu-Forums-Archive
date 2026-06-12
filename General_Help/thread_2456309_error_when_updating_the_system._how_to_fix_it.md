---
title: "error when updating the system. how to fix it?"
date: 2021-01-09
forum: General Help
---

### Post by ronjjjg8885 on 2021-01-09
hi
i get this error when updating the system.
why?
thanks[ATTACH=CONFIG]287705[/ATTACH]

---

### Post by ronjjjg8885 on 2021-01-09
also: now i can only boot with the recovery mode 
i don't know why

---

### Post by Impavidus on 2021-01-09
Can you boot an older kernel? Do you actually need the 5.8 kernel supplied by the hwe package, or does the standard 5.4 kernel work too?

It appears this is a common problem this week.

---

### Post by ronjjjg8885 on 2021-01-09
yes, i've tried the first recovery boot kernel and it booted but without the graphic driver so i couldn't really use it easily.
sorry i don't understand much about the things you wrote after.
it is good to know that i'm not the only one because then it would be harder to fix and spot the problem.
can you tell me where i can read about it and about the solutions...?

---

### Post by dino99 on 2021-01-09
Are you booting the latest hirsute kernel from proposed archive ?

it has now the required nvidia 460 driver:

linux (5.8.0-36.40+21.04.1) hirsute
* CVE-2021-1052 // CVE-2021-1053
    - [Packaging] NVIDIA -- Add the NVIDIA 460 driver

---

### Post by ronjjjg8885 on 2021-01-10
listen people
i've updated the updates of yesterday and now everything is ok and good like it was before
thank you for trying to help!

---

