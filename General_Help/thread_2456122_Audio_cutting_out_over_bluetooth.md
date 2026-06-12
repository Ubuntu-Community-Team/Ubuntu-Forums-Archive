---
title: "Audio cutting out over bluetooth"
date: 2021-01-04
forum: General Help
---

### Post by zviinz on 2021-01-04
Hello all, I've run into an issue that appeared seemingly out of nowhere. My audio is cutting out on my bluetooth headphones every minute or so. I'm not sure what's causing it and I've tried a few things I found online like increasing the headphone output buffer but nothing is working.

Looking at the syslogs I see a lot of 'temperature above threshold, cpu clock throttled..' alerts but my temps are not going near anything hot (constant 40c).

I'm a bit of a linux noob still so I'm not sure where else to look. For reference I'm using airpods pro. Any help is appreciated

```
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115679] mce: CPU0: Core temperature above threshold, cpu clock throttled (total events = 11)Jan  4 20:33:40 nuhtshack kernel: [ 5884.115680] mce: CPU4: Core temperature above threshold, cpu clock throttled (total events = 11)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115681] mce: CPU4: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115681] mce: CPU0: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115721] mce: CPU5: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115722] mce: CPU1: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115723] mce: CPU7: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115724] mce: CPU2: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115724] mce: CPU6: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.115725] mce: CPU3: Package temperature above threshold, cpu clock throttled (total events = 85)
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133826] mce: CPU0: Core temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133827] mce: CPU4: Core temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133828] mce: CPU2: Package temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133829] mce: CPU6: Package temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133829] mce: CPU4: Package temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133830] mce: CPU0: Package temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133833] mce: CPU3: Package temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133834] mce: CPU7: Package temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133874] mce: CPU5: Package temperature/speed normal
Jan  4 20:33:40 nuhtshack kernel: [ 5884.133875] mce: CPU1: Package temperature/speed normal

```

Thanks

---

