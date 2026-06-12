---
title: "Sudo doesn't work"
date: 2007-05-06
forum: General Help
---

### Post by Askeptykal on 2007-05-06
Okay, I think I know what I did... I edited the permissions on the /etc folder, and now everything is all buggy. When I try to use the sudo command in the terminal, I always get this message:

/etc/sudoers is mode 0666, should be 0440

I've done a bit of searching on the internet to help, but I haven't found too much... if I use the su command, it asks for the root password, and when I put it in, it gives me this message:

su: Authentication failure
Sorry.

Even though I put it in carefully and correctly. I've also tried the chmod command to change the permissions of the sudoers file, but I'm not permitted to perform that operation.

So, what do I do now?

---

### Post by taurus on 2007-05-06
You need to boot into recovery mode from GRUB menu and change the permission for /etc/sudoers back to what it was before.

```
chmod 440 /etc/sudoers
```
p.s.  Don't start changing permissions on files that you are not sure because they could and would crash your machine.

---

### Post by Askeptykal on 2007-05-06
Oh wow. That worked!

It almost makes me wish you could solve all of life's problems simply by entering a line of code.

Thanks so much for your help! I'll get the hang of all this eventually...

---

