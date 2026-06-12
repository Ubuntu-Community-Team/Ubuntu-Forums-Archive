---
title: "Synpatics driver edge motion property"
date: 2024-09-18
forum: General Help
---

### Post by nginmu on 2024-09-18
When did they stop including the edge motion property in the synaptics input driver? I tried rooting through synaptics-1.9.2/src/properties.c and I did find references to edgemotion_pressure, edgemotion_speed & edgemotion_always in there, but I'm not a C programmer so I'm not sure that just because they're mentioned in there, the feature is actually included.

I'd like to try and locate the lastest version of synaptics that still allows one to invoke edge motion.

[edit] found it - turned out to be version 1.6.1

---

