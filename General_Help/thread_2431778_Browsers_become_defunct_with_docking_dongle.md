---
title: "Browsers become defunct with docking dongle"
date: 2019-11-21
forum: General Help
---

### Post by treesloth on 2019-11-21
Hi.  Starting yesterday, I've run into a very strange problem.  I'm happily browsing along in Firefox when tabs become unresponsive.  Typically the state is induced by loading a tab.  When I attempt to do so, the loader icon in the tab spins and spins but doesn't work otherwise.  If I go to another tab and F5 it I get the same behavior.  If I try to close the browser I can't.  If I kill the process via CLI various of the Firefox processes close but other become defunct.  That result is the same whether I kill or kill -9... for whatever reason, Firefox gets into a state where it can't be cleared from the process table.  The usual response is to kill its parent process, but that's PID 1. :(  The outcome is the same in Chrome, but I've tested more thoroughly in Firefox.  Also, I can't reboot the system in this state.  I have to power down with the hardware switch and turn it back on.

On a hunch I disconnected my docking dongle.  It's not a full docking station, just a little 2"x2" Thunderbolt guy with Ethernet, HDMI, VGA, and USB.  When I rebooted I found that Firefox worked just fine with only the keyboard connected via USB.  I've also found that Windows 10, dual-booted on the same machine, works with no problems at all so far with the dongle connected.  Dmesg gave no relevant errors when I checked it.  I have noticed that when this happens the load average goes up without an apparent corresponding increase in CPU usage, which makes me think there are already blocked processes.

So... any suggestions on how to troubleshoot this?  I've gathered the information I can think of, but otherwise I'm at a loss on how to proceed.  Any tips would be appreciated.


OS:  Ubuntu 18.04 LTS
System:  Dell Precision 5510

---

