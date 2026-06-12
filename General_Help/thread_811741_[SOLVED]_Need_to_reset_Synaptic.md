---
title: "[SOLVED] Need to reset Synaptic"
date: 2008-05-29
forum: General Help
---

### Post by acron1 on 2008-05-29
I was trying to install Virtual Box (I need win for work) and something went wrong with the installation. The program appears to have installed but Synaptic is all messed up. Here is what I get when I open it.  Thanks.

---

### Post by overdrank on 2008-05-29
> **acron1 said:**
> I was trying to install Virtual Box (I need win for work) and something went wrong with the installation. The program appears to have installed but Synaptic is all messed up. Here is what I get when I open it.  Thanks.

Hi and I had a similar issue and I used this command 
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by acron1 on 2008-05-29
> **overdrank said:**
> Hi and I had a similar issue and I used this command 
```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

Thanks that worked.

---

