---
title: "Active kernel not installed according to Synaptic Package Manager"
date: 2015-11-11
forum: General Help
---

### Post by bob155 on 2015-11-11
):P   I'm having a boot full/can't upgrade issues. I've been fumbling around (learning) about removing unused kernels, orphaned packages of un-installed kernels, unresolvable package removal failures, and other fancy stuff, but now that I know enough to be dangerous, I REALLY don't get this. 

Or should I just go fishing.

14.04 LTS

Edit:  Tough to see but - Synaptic shows -49- as newest installed,   terminal shows -65-

Thanks!

[ATTACH=CONFIG]265482[/ATTACH]

---

### Post by ian-weisser on 2015-11-13
You have more repair work to do. You should be up to 68 when complete. Maybe 69 soon....

---

### Post by grahammechanical on 2015-11-13
You would think that Synaptic would list all the kernels in one block according to numerical order. But it just ain't so. Use the Synaptic search function to find Kernel 3.13.0-65-generic. By the way, the sudo update-grub command will list all the kernels for you.

Regards.

---

