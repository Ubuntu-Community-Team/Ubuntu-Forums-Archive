---
title: "Actualize the Repos"
date: 2007-10-20
forum: General Help
---

### Post by asiersanmi on 2007-10-20
Hi, im new in ubuntu.
I'm trying to actualize my source.list but when i try to save the changes it sais that i don't have the priviledges.

Then i go tu users management and I see that i'm included in all the groups.

thanks

---

### Post by ThrobbingBrain66 on 2007-10-20
to open it (and be able to save it), use a the following command in a terminal:

```
gksudo gedit /etc/apt/sources.list
```

To edit system files, you need to give yourself temporary root permissions.  This is what sudo and gksudo are used for.

---

### Post by asiersanmi on 2007-10-20
I did that but the konsole sais that the comand gedit doesn't exist.

Thanks

---

### Post by ThrobbingBrain66 on 2007-10-20
I'm sorry, I didn't see you were using Kubuntu.

Use this command instead:

```
kdesu kate /etc/apt/sources.list
```

---

### Post by asiersanmi on 2007-10-20
It's ok doing that i can edit the file and save it but before it this error is viewed:

Error: "/tmp/ksocket-Asier" is owned by uid 1000 instead of uid 0.

but i go on updating the file.

But then in the adept it doesn't actualize anything, it gets blocked

If it is someone how could help me i'd be very grateful, thanks

---

