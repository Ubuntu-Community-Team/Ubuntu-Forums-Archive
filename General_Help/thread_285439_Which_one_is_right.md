---
title: "Which one is right?"
date: 2006-10-26
forum: General Help
---

### Post by d3v1ant_0n3 on 2006-10-26
I was playing around with Superkarama just now, and noticed, via one of the widgets, that my system seemed to be using 700-odd Mb of RAM, out of 768Mb. Which is much more than the previous widget I had on reported. So I loaded up a few other memory displaying widgets, and ran 'free' in CLI. And there was a massive descrepancy in the values.

So basically, which one is right? And why the variation? I'm aware of the way Linux caches RAM, and it's surely a good thing. But why do some things show so much free, and others show a different amount? Screenie attatched, specs in sig.

Thanks in advance for any pointers:D

---

### Post by magicfab on 2006-10-27
The one reporting the most memory free is most likely wrong. Ask the authors of the repsective tools / check the docs to see what info their read /where.

---

### Post by matthewstory on 2006-10-27
use top in the CLI to get a better picture of how each process is using memory

sudo top

---

### Post by IYY on 2006-10-27
> So basically, which one is right?

I'd put my money on the 'free' command.

---

