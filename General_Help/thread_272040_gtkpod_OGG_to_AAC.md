---
title: "gtkpod: OGG to AAC"
date: 2006-10-05
forum: General Help
---

### Post by alecjw on 2006-10-05
Is there any way of telling gtkpod to store my songs locally in OGG but convert them to AAC when transferring them to my iPod?

---

### Post by moore.bryan on 2006-10-05
*as far as i know, gtkpod simply tranfers... i've heard good things about [jripper]("http://jtagger.sourceforge.net/jripper/"), though, as a converter.  not that this entirely fits your needs, but you may like to look at [rockbox]("http://www.rockbox.org")... it replaces apple's firmware with its own and lets you play any format.*

---

### Post by skymt on 2006-10-05
I don't recommend Rockbox just yet. I have it on my iPod mini, and it crashes a *lot*. It seems that a patch is on the way, but it is basically unusable right now.

Amarok can transcode OGG to AAC automatically when you transfer. I think you have to do it manually with any other transfer program.

---

### Post by moore.bryan on 2006-10-05
> I don't recommend Rockbox just yet. I have it on my iPod mini, and it crashes a *lot*. It seems that a patch is on the way, but it is basically unusable right now.
*i've got rockbox on my nano and it's saved my life :-)  never crashed once... what happens?  does it just blank out?*
> Amarok can transcode OGG to AAC automatically when you transfer. I think you have to do it manually with any other transfer program.
*totally true... i always forget about amarok since i dumped it because i hogged my limited resources... ;-)*

---

### Post by skymt on 2006-10-05
> **moore.bryan said:**
> i've got rockbox on my nano and it's saved my life :-)  never crashed once... what happens?  does it just blank out?

It just freezes. A lot of people have the same problem, see the [bug report](http://www.rockbox.org/tracker/task/5264).

---

### Post by moore.bryan on 2006-10-06
*see, i only have a 4gb nano... you lucky ducks with the 60gb colors!  ;-)  sorry to hear about the problem.  has rockbox advanced the issue at all?  their mailing list is pretty responsive about macgyver fixes; have you tried them?*

---

### Post by skymt on 2006-10-06
> **moore.bryan said:**
> *see, i only have a 4gb nano... you lucky ducks with the 60gb colors!  ;-)  sorry to hear about the problem.  has rockbox advanced the issue at all?  their mailing list is pretty responsive about macgyver fixes; have you tried them?*

The crash isn't limited to 60 gig photos. Mine is a 4 gig mini, but the symptoms are the same as others described, so I assume it's the same bug. It looks like a fix is being worked on, but I don't think it's in CVS yet.

---

### Post by moore.bryan on 2006-10-06
*have you filed another bug report?  since each of the pods has a different rockbox firmware contruct, your bug could be something much different than the 60gb one.*

---

### Post by alecjw on 2006-10-06
> **skymt said:**
> 
Amarok can transcode OGG to AAC automatically when you transfer. I think you have to do it manually with any other transfer program.

Thans, but what do you mean by "manually"? Do you mean convert them first with a converter then copy it  accross or you just have to tell it how to compess AAC, then it will do it automatically?

---

### Post by skymt on 2006-10-06
> **alecjw said:**
> Thans, but what do you mean by "manually"? Do you mean convert them first with a converter then copy it  accross or you just have to tell it how to compess AAC, then it will do it automatically?

As far as I know, you have to convert them first. Try installing nautilus-script-audio-convert, to do it from Nautilus. It's in Synaptic.

---

