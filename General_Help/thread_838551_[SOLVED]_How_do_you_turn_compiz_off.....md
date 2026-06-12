---
title: "[SOLVED] How do you turn compiz off?...."
date: 2008-06-23
forum: General Help
---

### Post by RadarBat on 2008-06-23
I installed Compiz from Forlong's Blog:

[http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074](http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074)

There is an entry at System >> Preferences >> Advanced Desktop Effects Settings, but there is no icon that allows me to turn Compiz off and turn Metacity on. Where/how do I get the icon? I cannot turn Compiz off to run other programs that don't agree with Compiz.

---

### Post by isaacj87 on 2008-06-23
Hey there,

What version of Ubuntu are you using? Feisty (7.04), Gutsy (7.10), Hardy (8.04)? If it's Gutsy or later, Compiz Fusion is installed by default...

Now to answer your question, the "Fusion-Icon" is located under Applications->System Tools. Or alternatively, you can press alt+F2 and type:

```

metacity --replace
```

Let me know how it goes!

---

### Post by RadarBat on 2008-06-23
I am running 8.04 64-bit. There is NO Fusion Icon in any menu. If I use:
metacity --replace
to turn compiz off, how do I turn it back on?

---

### Post by isaacj87 on 2008-06-23
Hmm, sorry I was careless in my reading! 

Okay this should install the Fusion-Icon for you:

```

sudo apt-get install fusion-icon
```

Then, it should be under Applications->System Tools

---

### Post by Doji on 2008-06-23
In 8.04 just go to System > Preferences > Appearance > Visual Effects and choose None to turn it off. The Fusion-Icon works too, but I like conserving space on my panel 8-).

---

