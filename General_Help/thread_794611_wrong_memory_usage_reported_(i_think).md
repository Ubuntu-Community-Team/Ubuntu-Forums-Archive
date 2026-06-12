---
title: "wrong memory usage reported (i think)"
date: 2008-05-14
forum: General Help
---

### Post by supersonicdarky on 2008-05-14
free reports:
```
             total       used       free     shared    buffers     cached
Mem:       1932840    1902976      29864          0      30060     879128
-/+ buffers/cache:     993788     939052
Swap:       979956      40548     939408

```
conky reports:
1.82gb/1.84gb

htop reports:
970mb/1887mb

gnome-system-monitor reports:
970.9mb/1.8gb

clearly something is reporting the memory incorrectly. I'm quite sure that ~900mb is the correct reading as I am running openbox, not a desktop environment.

lshw -C memory just in case:
```
  *-memory
       description: System Memory
       physical id: 2e
       slot: System board or motherboard
       size: 2GiB
     *-bank:0
          description: DIMM 667 MHz (1.5 ns)
          product: None
          vendor: None
          physical id: 0
          serial: None
          slot: A0
          size: 1GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:1
          description: DIMM 667 MHz (1.5 ns)
          product: None
          vendor: None
          physical id: 1
          serial: None
          slot: A1
          size: 1GiB
          width: 64 bits
          clock: 667MHz (1.5ns)
     *-bank:2
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 2
          serial: None
          slot: A2
          width: 64 bits
     *-bank:3
          description: DIMM [empty]
          product: None
          vendor: None
          physical id: 3
          serial: None
          slot: A3
          width: 64 bits

```

ask for anything else if needed. never happened in gutsy. memory reported properly on laptop.

---

