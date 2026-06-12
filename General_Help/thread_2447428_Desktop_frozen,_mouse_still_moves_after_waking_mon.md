---
title: "Desktop frozen, mouse still moves after waking monitor from sleep"
date: 2020-07-18
forum: General Help
---

### Post by accessd on 2020-07-18
Hi all,

This past week, after waking up my display in the morning after a period of inactivity, I find my desktop frozen (can't click anything, move windows, user the Super key or Alt-Tab), though the mouse still moves and I can kill the X server with Ctrl-Alt-Backspace and switch between terminals with Ctrl-Alt-FX. This just started happening after working perfectly for a long time, so I figure it was a result of a package upgrade, but I'm not sure which one. The Xorg.0.log file does not display anything relevant and journalctrl keeps logging the whole time and I'm not sure when in the middle of the night the freeze occurs, so I'm not sure what to look for. I tried switching to Wayland as I thought it might be an X Windows issue, but it put the display to sleep and I could not wake it by hitting any keys or moving the mouse and was forced to do a hard reboot (not sure if the problem is related as I've never used Wayland before).

I'm starting to think it's a Gnome issue but I have no idea how to diagnose it. I'm running Ubuntu 20.04. All the packages are up to date. The computer is running an Intel® Core™ i7-4790K CPU @ 4.00GHz × 8  CPU with a Radeon RX 560 Series (POLARIS11, DRM 3.35.0, 5.4.0-40-generic, LLVM 10.0.0) graphics card (using the open source drivers). Has anyone seen this issue or know how I might go about figuring out what is going on?

---

### Post by Bashing-om on 2020-07-18
accessd; Hello -

Humm, as you can activate a terminal - and switch terminals- it indicates that the kernel is consistent. Looking then as this is user space issues.
Though I think it doubtful that the radeon driver is broke - check it anyway:
```

sudo lshw -C display

```
If a graphic's driver is loaded, then ->

Also might be good to see what results in a "test" user account.
create a testing account:
```

sudo adduser --gecos '' testuser

```
and see if you can login to that.
Here we isolate to a config issue in "you" account.

[INDENT][INDENT]maybe Yes
[/INDENT][/INDENT]

---

### Post by accessd on 2020-07-18
Thanks for the suggestions. I get the following output from lshw -C display:

```
  *-display                 
       description: VGA compatible controller
       product: Baffin [Radeon RX 550 640SP / RX 560/560X]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: cf
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=amdgpu latency=0
       resources: irq:29 memory:e0000000-efffffff memory:f0000000-f01fffff ioport:e000(size=256) memory:f7e00000-f7e3ffff memory:c0000-dffff
```

Creating a test user account is a good idea. I'll give it a try and report back.

Thanks again

---

### Post by Bashing-om on 2020-07-18
accessd; Uh Huh .

Appears that the correct driver is loaded: per -
[https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)

will await what a new user account will reveal.

[INDENT][INDENT]Looking for what may be
[/INDENT][/INDENT]

---

### Post by accessd on 2020-07-20
Hi Bashing-om,

As suggested, I created a new user account, logged in and let it run throughout the night. In the morning, the display woke up and the desktop functioned as normal. Given that my account has not made it through the night without freezing for the past week or so, I suspect that you are correct that it is an issue with my account in particular. Do you have any ideas as to how I might go about diagnosing it?

---

### Post by Bashing-om on 2020-07-20
accessd; -

> 
an issue with my account in particular. Do you have any ideas as to how I might go about diagnosing it?


Not really as I run xfce and have very limited experience/skills with Gnome. If others here that do have these skills do not chime in - well - I can help you poke at it and see what we work out. Might be a lot of floundering about.

[INDENT][INDENT]We do what we have to do
[/INDENT][/INDENT]

---

### Post by accessd on 2020-07-21
No worries. I appreciate your help. I'm going to try disabling extensions to see if one of them is causing the problem.

---

### Post by Bashing-om on 2020-07-21
accessd; Hey -

> 
 I'm going to try disabling extensions to see if one of them is causing the problem.


Yup - I have seen where this can be a cause. For sure worth trying.

[INDENT][INDENT]still here, after all this time
[/INDENT][/INDENT]

---

