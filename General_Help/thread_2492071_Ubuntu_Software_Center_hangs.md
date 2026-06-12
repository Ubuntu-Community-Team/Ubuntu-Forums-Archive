---
title: "Ubuntu Software Center hangs"
date: 2023-10-29
forum: General Help
---

### Post by paulshaffer4 on 2023-10-29
Ubuntu 22 lts

Ubuntu Software Center hangs.  If I go to search for a program or click "installed," the little circle spins indefinitely.

Is there a terminal command to clear it's cache or something to get it working properly?

---

### Post by #&amp;thj^% on 2023-10-29
Well you can try this:
```
killall snap-store
```
But I don't use GUI's for installing software.
I just use Apt at CLI.

---

### Post by Rubi1200 on 2023-10-29
Hi,

In the terminal:

```

sudo apt clean
sudo apt update
```

---

### Post by paulshaffer4 on 2023-10-29
> **Rubi1200 said:**
> Hi,

In the terminal:

```

sudo apt clean
sudo apt update
```


Entered both in terminal, but still it hangs...... hmm.....

---

### Post by paulshaffer4 on 2023-10-29
> **1fallen said:**
> Well you can try this:
```
killall snap-store
```
But I don't use GUI's for installing software.
I just use Apt at CLI.


That worked.

Marking as solved.

Thank you!

---

