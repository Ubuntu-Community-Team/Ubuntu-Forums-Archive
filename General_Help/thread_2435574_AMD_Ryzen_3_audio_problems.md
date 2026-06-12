---
title: "AMD Ryzen 3 audio problems"
date: 2020-01-22
forum: General Help
---

### Post by ra7411 on 2020-01-22
[COLOR=#000000][FONT=Arial]This is about a new desktop computer build using AMD ryzen 3 cpu and msi 450 tomahawk mobo.

 1] there's a constant buzzing and crackling audio feed coming through. It sometimes correlates with activity on the HDMI screen - in other words when I move my mouse around or pull up a new window up additional audio static correlates with the things going on with the HDMI.

I'm using the back panel audio plugs going into an amp, the screen I'm using is HDMI, the same setup I was using with the machine this one replaces which did not have these problems.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]2]  I keep getting a message saying the screen resolution is [/FONT][/COLOR][COLOR=#000000][FONT=Arial]1920x1080 at *50* megahertz and should be [/FONT][/COLOR][COLOR=#000000][FONT=Arial]1920x1080 at *60* megahertz.  W[/FONT][/COLOR][COLOR=#000000][FONT=Arial]hen I check it ubuntu says it is already is  [/FONT][/COLOR][COLOR=#000000][FONT=Arial]1920x1080 at *60* megahertz.

I updated the bios, but it didn't change anything. I'm running the latest kernel 5.3.0-26-generic smp mod_unload.

Is this a graphics driver problem? I'm now running X.org v 1.20.5.

What's going on?
THanks



[/FONT][/COLOR]

---

### Post by CatKiller on 2020-01-22
> **ra7411 said:**
> [COLOR=#000000][FONT=Arial]there's a constant buzzing and crackling audio feed coming through. It sometimes correlates with activity on the HDMI screen - in other words when I move my mouse around or pull up a new window up additional audio static correlates with the things going on with the HDMI.

[COLOR=#000000][FONT=Arial]I'm using the back panel audio plugs going into an amp, the screen I'm  using is HDMI, the same setup I was using with the machine this one  replaces which did not have these problems.[/FONT][/COLOR]
[/FONT][/COLOR]

That's a hardware issue: insufficient shielding or isolation between the electronics on your motherboard and the onboard sound.

Having a shared earth between your computer and your amp, or having a ground lift on your amp, might help a bit. Otherwise, USB sound cards are generally inexpensive and will be isolated from the electrical noise that your motherboard is putting out, or you could take the sound output from your monitor if it supports that.

---

### Post by ra7411 on 2020-01-22
> **CatKiller said:**
> That's a hardware issue: insufficient shielding or isolation between the electronics on your motherboard and the onboard sound.

Having a shared earth between your computer and your amp, or having a ground lift on your amp, might help a bit. Otherwise, USB sound cards are generally inexpensive and will be isolated from the electrical noise that your motherboard is putting out, or you could take the sound output from your monitor if it supports that.

Good call.
Yesterday when I was building this thing, I noticed the Rosewill case audio line to the mobo had its shielding end about 1 in. before the plug, and the plug had some metal showing - I put some wraps of rubber tape around both and that seems to have cured the static problem.

BIOS still thinks the screen is at 50mHz tho....

---

