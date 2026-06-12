---
title: "cpufreq issue"
date: 2008-03-18
forum: General Help
---

### Post by noremac on 2008-03-18
While he was in town, I had a friend set up cpufreq and the ability to change it from the applet on the panel. I had tried to set it up earlier, however had issues making it work. He got it all working and was working beautifully at that. However upon a restart of the computer, it no longer is working.
Once started, it gave me two pop ups  of issues, one being that the applet did not find CpuFreq support in the sysfs. I added "powernow-k8" to my /etc/modules and that fixed that particular problem. This now allows the applet to show what the current CPU Freq is at. And being that it goes back and forth from different frequencies, I assume its on the mode to auto adjust. 

The second pop up however says that "The daemon in charge of changing the CPU speed in not started." I have enabled and started cpudynd service however that has not fixed my problem. I am not all that familiar with this and don't know what next to do or try.
Is there a particular daemon that still requires starting that I am just not aware of?
Let me know of any other information you can use, and I appreciate any help.

-Cameron

---

### Post by noremac on 2008-03-18
This is interesting. I just tried running the command "sudo cpufreq-selector -g performance" to manually change it. The icon in the panel does change to the perormance icon rather than powersaving. It stays there for a longer time than usual but then still after a few seconds switches back to auto/powersaving. 

I think it should be staying on performance after I type that in, or so I thought.
-C

[edit] Also, if I try to select a fixed CPU frequency at the command line, such as "sudo cpufreq-selector -f 2000000" it will go to that fixed freq for maybe 10-15 seconds, then go back to the ondemand setting. If I "cat scaling_governors" the only result in that file is "ondemand." Shouldn't there be more options in there?[/edit]

[edit again!] Ok, I have been able to stop the "ondemand" by stopping the service cpudynd. So now I can manually change the cpufreqeuncy from the command line and it will stay wherever I put it. So now the only question is how to get the applet working again. What daemon is it that I am needing to run? I am using the emifreq-applet on the panel[/edit]

---

### Post by noremac on 2008-03-20
bump

---

