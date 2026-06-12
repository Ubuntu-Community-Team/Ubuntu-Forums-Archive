---
title: "Kernel compilation help"
date: 2007-06-06
forum: General Help
---

### Post by borahshadow on 2007-06-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/108971](https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/108971) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				First I hope this is the right place I didn't know where to post this
Ok I have a brandnew mother board that I used to build a home server-workstation it is based off a nvidia MCP61
I would have put feisty on it except for this bug [108971]("https://bugs.launchpad.net/ubuntu/+source/mdadm/+bug/108971") so i decide to downgrade to edgy 
unfortunately edgy's kernel did not have a new enough forcedeth driver for my onboard NIC so I just put in a spare I had laying around and that is what I'm using now but I was also having problems with my printer that works fine on other computers (I wanted to share the printer) I finally figured out that it must be a buggy parallel port driver which would be due to the older kernel. Sound while not a big deal also does not work due to the older kernel not having support for the brand new MCP61 also I can't enable DMA while this is also not a huge issue I think it is because of the new mother board there are probably other things that aren't working correctly because of the older kernel so I decided I needed to compile a new kernel which would fix these problems
but every kernel I compile hangs at starting raid devices
I've tried compiling with the config from the current kernel and not changing anything and it does it I've tried changing the raid things to be compiled right in and not as modules and that doesn't work I just can't get it to work with my RAIDs err that is the reason I'm on edgy :( 
I've tried with 2.6.21.3 2.6.21-git6 2.6.21 2.6.20 it really would be good for me to have this compiled
are there some kind of raid patched ubuntu adds to their kernel?
could I somehow use feisty's kernel? 
or mabey I'm just doing something wrong
ps my kernel's compile fine but they just don't boot fine

---

### Post by borahshadow on 2007-06-07
bump
anybody?:sad:

---

### Post by shae on 2007-06-07
you can download the package that contains fiesty's kernel source with ubuntu patches from here: [http://packages.ubuntu.com/feisty/devel/linux-source-2.6.20]("http://packages.ubuntu.com/feisty/devel/linux-source-2.6.20")

---

### Post by borahshadow on 2007-06-07
I'll try that and post if it helps/works
Thanks

---

### Post by borahshadow on 2007-06-08
I tried that and it still hangs opon boot
I'll try again tommorrow and maybe post some more info about where it hangs but I think it hangs in the same spot I didn't have time to do much testing though

---

