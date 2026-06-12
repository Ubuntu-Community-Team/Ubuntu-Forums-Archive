---
title: "Need help with missing values in GKrellm"
date: 2019-11-04
forum: General Help
---

### Post by phuong112 on 2019-11-04
[COLOR=#000000]I have a strange thing happening with my GKrellm installation over time on four computers. For some reason I keep losing the cpu % utilization value in several cpu panels. The graphs display but that is all that is in the panel. Right now on this computer I have CPU6, CPU9 and CPU10 not labeled for percentage of utilization. And just today I lost the utilization value of the composite cpu panel at the top of the application.[/COLOR]

[COLOR=#000000]On another computer I am missing the utilization for cpu6. And another computer is missing the utilization for cpu0.[/COLOR]

[COLOR=#000000]I have never been able to find anything in the GKrellm configuration menus that changes the appearance or visibility of the utilization printout in the panel. I can change the graphing to split user and system, but nothing toggles the utilization off and on. I have reinstalled GKrellm several times and never been able recover the lost numbers. Obviously, there are configuration files leftover after a uninstall that I am missing.[/COLOR]

[COLOR=#000000]Anyone else having this issue and have figured out a solution?[/COLOR]

---

### Post by Mark Phelps on 2019-11-04
I only know of four configuration files with gkrellm -- and they are all in the .gkrellm2 folder (from what I recall).

Also, when I manually make config changes, I only see one of the files getting updated.

So, I don't believe there are any other gkrellm config files.

---

