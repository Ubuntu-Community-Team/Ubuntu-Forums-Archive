---
title: "Downgrading the kernel (2.6.12-9-386 to 2.6.10-5-386), help?"
date: 2005-10-23
forum: General Help
---

### Post by 5-HT on 2005-10-23
Hi,

I recently did a clean install of breezy but was having a few problems with the kernel (2.6.12-9-386) not letting my install from cd, and boot once installed.

I managed to get it to work, but this unfortunately required me to disable ACPI and use irqpoll (any ideas what that one does?) as boot options.

In Hoary, ACPI worked beautifully and there was no need for that irpoll boot option either...so I'd like to install the kernel used in Hoary (2.6.10-5-386) if that's possible but was wondering about two things:

1.I'm guessing that in order to do so I should change my sources.list to look in the hoary repos and install with apt/aptitude/synaptic?

If I went another way, say just downloading the .deb's for the linux-386, linux-image, and linux-restricted modules....should I dpkg -i them all, or would the linux-386 simply take care of the image, restricted modules, and updating GRUB?

2. Are there any problem, conflicts, etc. in downgrading the kernel from that tested in Breezy to the one used in Hoary?


Thanks for any help, in terms of anything to do about the kernel...I'm completely clueless but slowly reading up.

---

### Post by darknuala on 2005-11-16
downgrading a kernel will surely trash your system.  Why not just use Hoary, and install later package versions through the backports?

---

### Post by 5-HT on 2005-12-02
Sorry for the delayed response, thought this thread was forgotten about after it sunk quite rapidly.

Thanks for your help!

Thinking about it more, I don't see much difference between either sticking with hoary using backports or sticking with the kernel used in hoary. I guess in both cases, while it would alleviate my problems with breezy and the new kernel, I would still possibly limit myself in the future if I I continued to use this computer and the issues with it and the newer kernels were not ironed out.

With respect to that, I did a bit of research and found a few other people people experiencing the exact same issues who also filed a bug reports for the kernel.

So hopefully this issue may be fixed, but if not I guess the best course is to simply use the effective boot options and deal with the consequences.

Ever since I've switched to this operating system, I've simply been amazed with ubuntu specifically and linux in general, so I'm more than happy to deal with some issues.


In terms of my main question of whether it would be safe to use the old hoary kernel though, you did mention that it would most likely cause problems. I'm just wondering if that is due to possible conflicts with newer program requirements/dependencies, or am I missing the point entirely?

Anyways, I'll heed your advice and not do the downgrade.
Thanks again for your help!

---

