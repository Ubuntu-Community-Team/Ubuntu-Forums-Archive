---
title: "System monitor CPU% not matching top values"
date: 2022-02-15
forum: General Help
---

### Post by hateregistering on 2022-02-15
Why does System monitor program not display same values as top program.
Ubuntu version : Ubuntu 20.04.3 LTS
[ATTACH=CONFIG]290041[/ATTACH]

---

### Post by Impavidus on 2022-02-16
1: They take averages over slightly different times.
2: Top shows as a percentage of capacity per CPU core, System monitor as a percentage of total capacity. Under full load, the percentages of System monitor add up to 100%, but those of top add up to 100% times the number of CPU cores. It looks like you've got about 12 cores.

---

