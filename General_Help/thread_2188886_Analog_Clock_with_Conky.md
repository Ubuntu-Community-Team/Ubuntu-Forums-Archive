---
title: "Analog Clock with Conky"
date: 2013-11-19
forum: General Help
---

### Post by os2 on 2013-11-19
Is there an analog Conky script which acript which doesn't use LUA?

How can I create one from text alone or adapt xclock somehow?

Thx!!

---

### Post by stinkeye on 2013-11-20
> **os2 said:**
> Is there an analog Conky script which acript which doesn't use LUA?

How can I create one from text alone or adapt xclock somehow?

Thx!!
Yep, a while ago Timo created an analog clock using fonts.
[ATTACH=CONFIG]247945[/ATTACH]

[**_[COLOR="#B22222"]Conky PitStop[/COLOR]_**]("http://conky.pitstop.free.fr/wiki/index.php5?title=Clocks_1_to_9_(en)")

Why don't you want to use lua?

---

### Post by os2 on 2013-11-20
Thanks that looks like an interesting approach.

I was interested in a minimalist approach rather than piling scripts upon scripts. So I wished to avoid LUA in favour of something simple.

---

### Post by stinkeye on 2013-11-20
> **os2 said:**
> Thanks that looks like an interesting approach.

I was interested in a minimalist approach rather than piling scripts upon scripts. So I wished to avoid LUA in favour of something simple.

For analog clocks lua is the best way to draw the hands.
The attached pic shows some of the analog clock conkys I have.

The bottom left clock is pure lua while the rest use clockface images and lua to draw the hands.

The attached vid shows the cogs in the top left clock moving and some of the 57 different clockfaces for the bottom right clock.

---

### Post by os2 on 2013-11-20
^^^ You're a Clockwork Artisan.

Let me decide what to do with it.

---

