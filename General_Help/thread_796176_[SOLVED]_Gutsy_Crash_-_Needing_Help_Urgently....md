---
title: "[SOLVED] Gutsy Crash - Needing Help Urgently..."
date: 2008-05-16
forum: General Help
---

### Post by robelliott2125 on 2008-05-16
Hey guys,

After a two week return back to winblows expeee, I've returned back to Ubuntu.  I missed all the programs and the pure speed!

I've got one prob though...

While running ```
sudo apt-get upgrade
``` my system crashed, so I had to hard reboot the system (forgot about ctrl, alt and backspace), so since restarting, I now can't update anything, access Synaptic Package Manager or anything else.

Can someone help?

Thank you

---

### Post by kpkeerthi on 2008-05-16
What happens when you run this command from terminal ?
```
sudo aptitude update
```
Post back error messages, if any.

---

### Post by robelliott2125 on 2008-05-16
> **kpkeerthi said:**
> What happens when you run this command from terminal ?
```
sudo aptitude update
```
Post back error messages, if any.

Sorry!  lol

Usually helps when i say whats happening.

I'm now getting:

```

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
```

When trying to run ```
dpkg --configure -a
```

It comes up with:

```
robert@robert-desktop:~$ dpkg --configure -a
dpkg: requested operation requires superuser privilege

```

---

### Post by kpkeerthi on 2008-05-16
Run that command with 'sudo' as in
```
sudo dpkg --configure -a
```

This should clear things up. Close synaptic / Add-Remove programs if they are running.

---

### Post by robelliott2125 on 2008-05-16
> **kpkeerthi said:**
> Run that command with 'sudo' as in
```
sudo dpkg --configure -a
```

This should clear things up. Close synaptic / Add-Remove programs if they are running.

lol, I didn't even think of that!!!  Sorry, two weeks seems to have fried my brain...  Plus I was a linux n00b to begin with.  But thank you!!!  Seems to be sorting itself out now.

```
sudo apt-get install brain
```

Now to find the Solved bit...  :guitar:

---

