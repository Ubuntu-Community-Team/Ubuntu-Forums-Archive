---
title: "ubuntu won't boot up..."
date: 2008-04-26
forum: General Help
---

### Post by Mia_tech on 2008-04-26
after installing a new nvidia 6200 video card, my ubuntu install won't boot up... it stops at loading hardware drivers....how can I fix this?.. is there any way to boot into ubuntu, and fix this?...also I've tried to boot into a live cd and I get the same error, it won't boot to the x session...if someone could give me hand, I appreciate

thanks

---

### Post by LaRoza on 2008-04-26
> **Mia_tech said:**
> after installing a new nvidia 6200 video card, my ubuntu install won't boot up... it stops at loading hardware drivers....how can I fix this?.. is there any way to boot into ubuntu, and fix this?...also I've tried to boot into a live cd and I get the same error, it won't boot to the x session...if someone could give me hand, I appreciate

thanks

Boot into the recovery console and run:

```

dpkg-reconfigure -phigh xserver-xorg

```

---

### Post by Mia_tech on 2008-04-26
yeah that's part of the problem I can't even get to the prompt in recovery mode or any other way...

thanks

---

