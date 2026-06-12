---
title: "apt-get install - stylistic choice &quot;[Y/n]&quot;"
date: 2013-01-03
forum: General Help
---

### Post by histamineblkr on 2013-01-03
I have an odd question about the output in apt-get install. If you run the command:

```

apt-get install atris

```your next prompt would be:

```

Do you want to continue [Y/n]? 

```Can anyone tell me why "[Y/n]" was chosen rather than "[y/n]" or "[Y/N]"? I can put either a "Y" or "y" and it will take either input correctly. Also I can "N" or "n" and it will function correctly. Is it purely a stylistic choice or something else?

Thanks to anyone who takes time to answer my odd question.

---

### Post by ibjsb4 on 2013-01-04
"[Y/n]" means that if you press enter at that point, "yes" will be automatically selected.

---

### Post by histamineblkr on 2013-01-04
> **ibjsb4 said:**
> "[Y/n]" means that if you press enter at that point, "yes" will be automatically selected.

Ah so by capitalizing the "Y" it means that when you hit enter it is chosen by default?

---

### Post by SeanBlader on 2013-01-04
> **histamineblkr said:**
> Ah so by capitalizing the "Y" it means that when you hit enter it is chosen by default?

Yes. If the option said [y/N] you'd have to specifically do "y", "Y", or "yes" in any case for it to work. I believe it's not case sensitive, well that's how I'd do it if I wrote it.

Anyway, in the UI field that's called "feed forward" information. It's like a hover or a cursor change when you mouse over something, it's telling you that there's something that happens if you do something in that case. Next time you see it, check and see what happens if you type in q, x, or maybe m. Never bothered myself, but now I'd be curious to see what it did. Again if I wrote it, I'd prompt you again for a clearer answer to my question.

Computer: "Do you want to install this to your hard drive?"

Me: "Albuquerque"

Computer: "I'm sorry that doesn't really answer my question."

---

