---
title: "Getting trouble with Sudo permissions"
date: 2012-11-29
forum: General Help
---

### Post by dmahesh22 on 2012-11-29
When I've give "sudo bash" in terminal, following error message is displaying

sudo : /etc/sudoers is mode 0555, should be 0440
sudo : no valid sudoers sources found,quitting
sudo : unable to initialize policy plugin

  What might be wrong, suddenly this message was showing.

---

### Post by pkadeel on 2012-11-29
> **dmahesh22 said:**
> When I've give "sudo bash" in terminal, following error message is displaying

sudo : /etc/sudoers is mode 0555, should be 0440
sudo : no valid sudoers sources found,quitting
sudo : unable to initialize policy plugin

  What might be wrong, suddenly this message was showing.
/etc/sudoers is by default 0440. you might have changed that accidentally
can you run other sudo commands? if yes then revert it back to 0440
```
sudo chmod 0440 /etc/sudoers

```

---

### Post by dmahesh22 on 2012-11-29
the above command is not working,because actual trouble with "Sudo".

      Thanks for reply

---

### Post by steeldriver on 2012-11-29
I think you will need to boot into the recovery console, remount the root filesystem read-write, and do the chmod from there

```
# mount -o remount,rw /
# chmod 0440 /etc/sudoers
# exit
```If you changed file modes on other stuff that you shouldn't (e.g. by doing a recursive chmod in the root filesystem) then other things may be broken as well though.

---

