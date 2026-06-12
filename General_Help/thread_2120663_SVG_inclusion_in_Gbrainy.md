---
title: "SVG inclusion in Gbrainy"
date: 2013-02-27
forum: General Help
---

### Post by Cyril4133 on 2013-02-27
Hi,

I tried to modify /usr/games/gbrainy/verbal_analogies.xml which worked fine.

But I am unable to include a svg despite the xml format. I have no picture with

```

	<analogy>
		<!--
			Translators, please check these recommendations when translating gbrainy: http://live.gnome.org/gbrainy/Localizing
		-->
		<_question type = "Standard">Which of the following sports does not belong in this group?</_question>
		<svg file="clock.svg" text="My text" />
		<_tip>Think of the items used in the game.</_tip>
		<_answer correct = "yes">Cycling</_answer>
		<_rationale>It is the only one that does not use a ball in the game.</_rationale>
	</analogy>

```

---

### Post by Cyril4133 on 2013-03-02
I have simply remove pipe symbol:

```
:map <F2> :wa <CR><esc> :make <CR><CR>
```

---

