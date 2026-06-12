---
title: "My wifi card goes out of 'managed' all the time!"
date: 2007-05-24
forum: General Help
---

### Post by loathsome on 2007-05-24
Hi there,

I'm able to set my Intel IPW3945 card into managed mode by doing ```
iwconfig eth1 mode managed
```, but then after 10-20 seconds It'll pop back into "monitored". Is there any way I can prevent this, or do I have to create a shell script that puts it back in every 10 seconds or so?

Thanks.

---

### Post by mbradlcu on 2007-05-27
would commenting out the card in the /etc/network/interfaces help?

---

### Post by loathsome on 2007-05-27
It's not even in there :) (due to a boot bug)

I've created a shell script that puts it back in , though, so it's no «big deal» right now.

---

