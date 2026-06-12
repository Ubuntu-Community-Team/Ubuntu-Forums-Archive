---
title: "W500 Thinkpad ACPI Temperature Sensors"
date: 2014-10-16
forum: General Help
---

### Post by RadiantPhoenix on 2014-10-16
My Thinkpad W500 was working fine with Ubuntu 12.04 and ThinkPad Fan Control (tpfanco) until recently.

Just today, it suddenly shut down with no warning. When I rebooted, it failed to start up, but it felt hot, so I let it sit for a while.

When I tried to start it up again later, it gave me some sort of error about "thinkpad acpi" whose details I have forgotten, but what I noticed immediately upon logging in was that _all of my temperature sensors indicated a temperature of zero_.

I think that what happened was that, because ThinkPad Fan Control was told that the computer was freezing cold, it turned the fans off, which would naturally cause the computer to cook itself.

Note: I also use the temperature sensor applet, and it also showed a temperature of zero

Summary:
System:
[LIST]
[*]Lenovo Thinkpad W500 
[*]Ubuntu 12.04 x64, regularly updated 
[*]ThinkPad Fan Control which I think is the version from the PPA, but I don't remember for certain because it was a long time ago. 
[/LIST]
What I did:
[LIST]
[*]Start up the computer 
[*]Check temperature sensor applet 
[*]Check ThinkPad Fan Control 
[/LIST]
What I expected:
[LIST]
[*]Both applications should show a temperature somewhere in the 20 to 70 degree Celesius range 
[*]ThinkPad Fan Control should have the fan running at some nonzero speed 
[/LIST]
What I got:
[LIST]
[*]Both applications showed a temperature of 0 degrees Celsius for all Thinkpad sensors. (the applet showed the hard drive at around 34 degrees Celsius, but ThinkPad Fan Control doens't detect that) 
[*]ThinkPad Fan Control showed the fan completely stopped 
[/LIST]

The computer shut itself down when it overheated, so I feel confident that the temperature sensors *work*, and it's a software problem. Which is actually somewhat unfortunate because if it were a hardware problem i could just send it in and get it fixed.

What should I do? (I'm posting from my other Thinkpad where the temperature sensors still work)

**EDIT: The problem appears to have disappeared as mysteriously as it appeared. I certainly didn't install any updates, I just left the computer powered off and sitting around for a while. The sensors are working again... for now.**

---

