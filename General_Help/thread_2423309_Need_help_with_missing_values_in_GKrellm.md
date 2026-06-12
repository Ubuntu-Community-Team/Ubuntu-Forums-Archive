---
title: "Need help with missing values in GKrellm"
date: 2019-07-20
forum: General Help
---

### Post by Keith Myers on 2019-07-20
I have a strange thing happening with my GKrellm installation over time on four computers.  For some reason I keep losing the cpu % utilization value in several cpu panels.  The graphs display but that is all that is in the panel.  Right now on this computer I have CPU6, CPU9 and CPU10 not labeled for percentage of utilization.  And just today I lost the utilization value of the composite cpu panel at the top of the application.

On another computer I am missing the utilization for cpu6.  And another computer is missing the utilization for cpu0.

I have never been able to find anything in the GKrellm configuration menus that changes the appearance or visibility of the utilization printout in the panel. I can change the graphing to split user and system, but nothing toggles the utilization off and on.  I have reinstalled GKrellm several times and never been able recover the lost numbers.  Obviously, there are configuration files leftover after a uninstall that I am missing.

Anyone else having this issue and have figured out a solution?

---

### Post by dragonfly41 on 2019-07-21
I have GKrellm installed .. so I have just run the command ..

sudo locate gkrellm

to find where all the config files are.
I saw some in /snap/core/...

---

### Post by Keith Myers on 2019-07-21
Thank you.  I have finally located where the files that control gkrellm are located.  I found a file called user-config located at /home/keith/.gkrellm2/ that contained a list of the cpus and their attribute.  The cpu panels that were missing the utilization had a 0 instead of a 1 in an attribute named cpu extra_info for each cpu.  The file says the file should not be edited.

### GKrellM user config.  Auto written, do not edit (usually) ###

But I went ahead and edited the cpu_extra_info attributes for the missing value panels and now I have all my utilization values back for all 24 cpus.

---

