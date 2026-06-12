---
title: "free shows I'm using swap even when there is memory available"
date: 2018-04-05
forum: General Help
---

### Post by davidsinfield on 2018-04-05
On Ubuntu 16.04.

I have the recurring problem of almost constant disk usage on my old asus aspire laptop. I've checked the disk and it is healthy.

I had a look at the output from free and although I have 663MB of memory available, I'm using 144MB of swap and I'm wondering if this is the issue.

Is this normal?

Can I prevent it?

```

~$ free -h -c 60 -s 100
               total        used        free      shared  buff/cache   available
Mem:           3.7G        2.2G        333M        592M        1.2G        663M
Swap:          5.3G        144M        5.1G



```

---

### Post by SeijiSensei on 2018-04-05
You can turn off swap with the command "sudo [swapoff]("https://linux.die.net/man/8/swapoff") -a".  You might want to see if that makes much difference.

That 1.2 G devoted to cache is used for disk caching.  It will expand or shrink as necessary as programs are loaded and unloaded.  I doubt swap is really the issue here.  Some other process is more likely the culprit.

---

### Post by cruzer001 on 2018-04-05
reduce swappiness

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

---

### Post by davidsinfield on 2018-04-05
Thanks SeijiSensei. 
It was fine until I tried to open my dev apps (bluefish, filezilla, chrome, fiddler) then everything locked up.
I'll try reducing the swappiness to a level where things work and the disk light goes off occaisionally.

Was also considering configuring a usb3 stick as my swap device if I can get one to benchmark quicker than my disk.

---

### Post by davidsinfield on 2018-04-05
> **cruzer001 said:**
> reduce swappiness

[https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F](https://help.ubuntu.com/community/SwapFaq#What_is_swappiness_and_how_do_I_change_it.3F)

Thanks for that. Really useful link.
See previous reply. I'll have a go with this and see what happens.

---

### Post by cruzer001 on 2018-04-05
Please post back if you need further assistance.

---

### Post by SeijiSensei on 2018-04-05
One thing you can try is opening a terminal and running "top".  Then open your normal suite of applications one at a time and watch how memory changes.

---

### Post by cruzer001 on 2018-04-05
You can fine tune "top" for high memory usage by pressing:

Shift + m

---

