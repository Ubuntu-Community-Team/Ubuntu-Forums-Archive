---
title: "Reset password instructions not working"
date: 2015-05-05
forum: General Help
---

### Post by Camilia on 2015-05-05
I am trying to reset the pc password. I tried the instructions at [psychocats]("http://www.psychocats.net/ubuntu/resetpassword") After retyping the new password got message Authentication manipulation error.

What else can I do? Please explain in detail.

---

### Post by steeldriver on 2015-05-05
Are you sure you didn't miss a step? that error usually indicates that the filesystem is not writeable: make sure you do

```

mount -o rw,remount /

```

before running the passwd command

---

### Post by Camilia on 2015-05-05
> **steeldriver said:**
> Are you sure you didn't miss a step? that error usually indicates that the filesystem is not writeable: make sure you do

```

mount -o rw,remount /

```

before running the passwd command
I did that. I got a lot of info that didn't make sense to me. Still can't reset my password.

---

### Post by steeldriver on 2015-05-05
Perhaps the info would make sense to one of us? can you post it please (or at least summarize)

---

### Post by Camilia on 2015-05-05
> **steeldriver said:**
> Perhaps the info would make sense to one of us? can you post it please (or at least summarize)
I wasn't able to copy it. I am just going to start over. It is quicker.

---

