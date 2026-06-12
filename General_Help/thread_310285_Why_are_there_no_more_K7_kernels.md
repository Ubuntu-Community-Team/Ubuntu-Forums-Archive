---
title: "Why are there no more K7 kernels?"
date: 2006-12-01
forum: General Help
---

### Post by ubuntu-mike022465 on 2006-12-01
Why was the decision made to toast the different types of kernels that were available in 6.06?  

 I had upgraded my laptop to Edgy, then when I tried to install say Abiword, I get an error message saying that my cpu arctitechure (?) is wrong (i386).  I know full well what my cpu is on my laptop: Athlon XP! 

 I would like to see a move BACK to individual kernels so that people can CHOOSE the instruction set that's meant for their particular processor.  

 And please save me the statement: "Build your own kernel". I've tried numerous times and have failed every time.  I have referenced as much online help as possible to no avail.

So a move back to cpu specific kernels would be a great step forward.

Thank you for creating the BEST distro around!

M.

---

### Post by Delkster on 2006-12-01
> **ubuntu-mike022465 said:**
> Why was the decision made to toast the different types of kernels that were available in 6.06?

Basically, the kernel is now compiled using generic optimization rather than CPU-specific ones. In tests no significant difference in performance was noticed between CPU-specific and generic ones, so a decision was made to use the generic optimizations. I assume that the main advantage is simplicity.

> I had upgraded my laptop to Edgy, then when I tried to install say Abiword, I get an error message saying that my cpu arctitechure (?) is wrong (i386).  I know full well what my cpu is on my laptop: Athlon XP!

Are you sure this has anything to do with kernels? In case you think it does, what kernel(s) do you have installed and in use right now?

---

### Post by ubuntu-mike022465 on 2006-12-01
> **Delkster said:**
> Basically, the kernel is now compiled using generic optimization rather than CPU-specific ones. In tests no significant difference in performance was noticed between CPU-specific and generic ones, so a decision was made to use the generic optimizations. I assume that the main advantage is simplicity.



Are you sure this has anything to do with kernels? In case you think it does, what kernel(s) do you have installed and in use right now?

I'm running the generic kernel that came with the LiveCD, 2.6.17-generic.

---

### Post by dcstar on 2006-12-02
> **Delkster said:**
> Basically, the kernel is now compiled using generic optimization rather than CPU-specific ones. In tests no significant difference in performance was noticed between CPU-specific and generic ones, so a decision was made to use the generic optimizations. I assume that the main advantage is simplicity.
.....

I can imagine that jobs the kernel does the majority of the time probably don't benefit too much from any CPU specific code, but I can imagine that some apps would.

Graphic intensive apps may well be better compiled with specific CPU optimisations, Firefox being an example with the Swiftfox versions compiled to take advantage of specific CPU graphics capabilities.

---

