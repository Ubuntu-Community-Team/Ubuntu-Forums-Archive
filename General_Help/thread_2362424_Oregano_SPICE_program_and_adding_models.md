---
title: "Oregano SPICE program and adding models"
date: 2017-05-28
forum: General Help
---

### Post by rdragonrydr on 2017-05-28
Hello. I am a computer engineering student, and my circuits class requires that I have a SPICE program. As a Ubuntu user, I would like to be able to use an open source program for this purpose.

I have installed oregano from the Ubuntu package repository, and I quickly found out that it is missing the model for a LM741 op amp (According to other posts, this is due to conflicting licenses).

I downloaded the model from Oregano's github page and moved it to /usr/share/oregano/models, and my original error message about being unable to find the op amp model disappeared, but it still won't simulate the circuit.

/home/rdragonrydr/pro1.oregano 
X_U1: can't find: LM741
### Too few or none analysis found ###

It shows the model file in properties if I right-click the op amp, but when trying to simulate it, it still fails.

I'd add the project file, but apparently, files are limited to 19.5k, and my file is 20. Great.

---

### Post by dragonfly41 on 2017-05-28
Amazing what you can find through a simple search ..

[https://askubuntu.com/questions/166929/how-do-i-add-more-models-to-oregano](https://askubuntu.com/questions/166929/how-do-i-add-more-models-to-oregano)

[https://github.com/drahnr/oregano/tree/master/data/models](https://github.com/drahnr/oregano/tree/master/data/models)

but the model LM741 in above site does not look like your file.

---

### Post by rdragonrydr on 2017-06-05
I actually visited both of these sites. That's how I got the model in the first place and found out about the problem.

However, what about

> [COLOR=#111111][FONT=Ubuntu]Again, the problem now is that unziping these two zipfiles, we have a huge collection of [/FONT][/COLOR]PSPICE[COLOR=#111111][FONT=Ubuntu]models without any linking with [/FONT][/COLOR]Oregano[COLOR=#111111][FONT=Ubuntu]'s library names (I was trying to use a [/FONT][/COLOR]TTL 7400b[COLOR=#111111][FONT=Ubuntu]component - a standard NAND gate - but I couldn't find the component in these two huge libraries, both searching for [/FONT][/COLOR]7400[COLOR=#111111][FONT=Ubuntu] and [/FONT][/COLOR]NAND[COLOR=#111111][FONT=Ubuntu]).[/FONT][/COLOR]

I got the file, and all the rest, from the github page linked, but as I said, it won't work. Would this be the issue, and how might I go about linking them? I can't imagine that they would all be in the code but not actually converted for compatibility, but something sure isn't working!

Otherwise, what do you think the issue might be?

**I already added the files (the github ones) to the model folder in Oregano. I have already read both of those pages, and they have not helped me.**

That said, thank you for attempting to help. I appreciate it, although the sarcasm was perhaps a bit unfair, since I had already done read both. However, if you can find any results on this that I missed, please do let me know.

---

### Post by dragonfly41 on 2017-06-06
> [COLOR=#000000]but as I said, it won't work. [/COLOR][COLOR=#000000]

I installed Oregano on Ubuntu 16.04 (although I don't need it) and got it to at least display LM741 opamp (see screenshot)
But I have not attempted going deeper since I am not versed in using Oregano (I will remove it after this experiment).
[/COLOR]I found that LM741 is in fact referenced inside /usr/share/oregano/libraries/opamplib.oreglib (open this as a text file to view).[COLOR=#000000]
However that does not explain why I could not find LM741.model file. [/COLOR]

---

