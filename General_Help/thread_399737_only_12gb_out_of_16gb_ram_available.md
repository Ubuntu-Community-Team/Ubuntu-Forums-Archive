---
title: "only 12gb out of 16gb ram available"
date: 2007-04-02
forum: General Help
---

### Post by snacktime on 2007-04-02
Installed our new db server using the edgy adm64-alternate cd so we could setup software raid.  Hardware is a quad core xeon with 16gb ram.

dmesg has this line:

Memory: 12280856k/14155776k available (2129k kernel code, 295988k reserved, 1424k data, 188k init)

top and vmstat both show 12gb available memory.  Post and bios both show 16gb.

What's going on?  

Chris

---

### Post by Happy_Man on 2007-04-02
Do you mean that it shows 12 gb ram TOTAL, or 12 gb ram AVAILABLE? 

On a less related note, how on earth did you get 12 gb of ram, leave alone 16?

---

### Post by snacktime on 2007-04-02
12gb total ram is what linux is seeing, although in dmesg it's showing 14gb available which I don't really understand.  4x4gb simms is what's in the box and what the bios and post show.

---

### Post by dguy on 2007-04-02
Out of curiosity, what's the output of running the free command?

On my 2gb laptop, I get:

```

             total       used       free     shared    buffers     cached
Mem:       2074696    2012332      62364          0      91464     832228
-/+ buffers/cache:    1088640     986056
Swap:      4096552      28328    4068224

```

But that's 32-bit Ubuntu... I've heard that 64-bit can address more memory, but can also use up more memory for programs that make heavy use of pointers, since they now require 8 bytes (64 bits) instead of 4.

---

### Post by snacktime on 2007-04-02
Well learn something new every day.  The bios has an option to disable/reserve portions of memory that will only be used if active memory fails.  By default it was set to reserve 4gb.  

Chris

---

### Post by dguy on 2007-04-03
Wow, that's good to know. I've never seen that one, but next time I buy or build a new machine, I'll have make sure to run through the BIOS settings first.

-Damien

---

