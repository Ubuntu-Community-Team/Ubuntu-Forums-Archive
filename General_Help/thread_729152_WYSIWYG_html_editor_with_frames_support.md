---
title: "WYSIWYG html editor with frames support?"
date: 2008-03-19
forum: General Help
---

### Post by bixejo on 2008-03-19
Hi all,

I'm looking for a WYSIWYG HTML editor that also provides support for web pages with frames.  I really like Kompozer interface and its general working, but I believe it does not support page frames. I tried also with some other WYSIWYG html editors, but found no frame support either.

Any suggestions on this would be greatly appreciated.

---

### Post by kyphi on 2008-03-19
I don't know about WYSIWYG editors - learning HTML code is not that difficult, in fact, it is a lot of fun.

Do have a look at [http://www.arachnoid.com/arachnophilia](http://www.arachnoid.com/arachnophilia)

It is a Java programme and is free.  It is also very good....and it does frames.

---

### Post by Wiifreak on 2008-03-19
Is there a program that is like ***cough*** Microsoft Frontpage ***cough***

Because Kompozer is a difficult program for me

---

### Post by bixejo on 2008-03-19
> **kyphi said:**
> I don't know about WYSIWYG editors - learning HTML code is not that difficult, in fact, it is a lot of fun.

Do have a look at [http://www.arachnoid.com/arachnophilia](http://www.arachnoid.com/arachnophilia)

It is a Java programme and is free.  It is also very good....and it does frames.

I know it's not that difficult, and in fact is what I must do right now to create pages with frames and also to fix little things that are rather difficult to manage in WYSIWYG editors. But the point is that my time is quite limited and have no enough life to learn all what I'd like.

I also considered Arachnophilia, but to the best of my knowledge it's not a WYSIWYG editor, and that's important for me to quickly develop pages.

So any other suggestions would be highly appreciated.

---

### Post by bixejo on 2008-03-19
> **Wiifreak said:**
> Is there a program that is like ***cough*** Microsoft Frontpage ***cough***

Because Kompozer is a difficult program for me
I don't believe you will be able to find a program that behaves **[COLOR=black]exactly[/COLOR]** like Microsoft Frontpage. Maybe you could try to make Frontpage work on Linux by using *wine* or some other similar emulation software, but I cannot help you in that as I haven't ever used those emulation programs.

I also used Frontpage and I feel Kompozer quite easy to use. I find the only drawback I mentioned in the starting thread post.

---

### Post by jamescowie on 2008-03-19
what i would say that your best solution to a wysiwyg editor for linux would be to use scite and firefox with firebug. it does mean that you will have to improve your knoledge of html but you will be able to transfer these skills to other projects in the future,

also im curious why are you using frames? do you mean iframes of oldskool frames.

jc.

---

### Post by Gordy on 2008-03-19
Have you tried NVU?

It is what I used for my site after spending hundreds of dollars on other WYSIWYG editors.

---

### Post by bixejo on 2008-03-19
> **Gordy said:**
> Have you tried NVU?


As far as I know, Kompozer is a (more or less) bug-free version of NVU that is now released under this name, as the NVU project has been abandoned. So, yes, I tried it :)

---

### Post by aysiu on 2008-03-19
Maybe you should find a way to take down the W3C website as well.

WYSIWYG editor to create frames? Yikes...

Please do the web a favor and use blogging software to create sites for you, hire someone to create sites for you, or learn CSS.

---

### Post by bixejo on 2008-03-19
> **aysiu said:**
> Maybe you should find a way to take down the W3C website as well.

WYSIWYG editor to create frames? Yikes...

Please do the web a favor and use blogging software to create sites for you, hire someone to create sites for you, or learn CSS.
Thank you for your wise advices, aysiu. I shall consider them with all the respect they deserve.

P.S.: By the way, I thought that ubuntuforums staff were supposed to be an example of good manners and respect to others. It's certainly disappointing to see that I was utterly wrong.

---

### Post by bixejo on 2008-03-19
Ok, just to clarify because it's possible it was not clear enough: when I talk about frames I refer to "framesets", like the following code:

```
<frameset cols="168,*">
  <frame name="sideframe" target="mainscr" src="sidefram.html">
  <frame name="mainscr" src="mainscr.htm" target="_self">
  <noframes>
  <body>
[COLOR=Gray]*   ... no frames page stuff here...*[/COLOR]
  </noframes>
</frameset>

```

---

