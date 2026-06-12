---
title: "Ubuntu Wiki Editing Syntax Documentation"
date: 2007-08-02
forum: General Help
---

### Post by Jamie Jackson on 2007-08-02
What wiki package does the Ubuntu Wiki use OR where is the syntax documentation for it?

Most specifically, I'm looking for how to create a code block...

```
...like this...
```

...that doesn't wrap. Turns out {{{this syntax}}} does wrap, and it's screwing up some documentation.

I've seen some of the non-editable documentation up there that does it right, but I can't see the source, so I don't know what syntax was used.

Thanks,
Jamie

---

### Post by nitro_n2o on 2007-08-02
MoinMoin [https://help.ubuntu.com/community/MoinMoin](https://help.ubuntu.com/community/MoinMoin) :)

---

### Post by Jamie Jackson on 2007-08-02
Okay, I surfed around a little from your link and found [this]("http://moinmoin.wikiwikiweb.de/HelpOnFormatting"). Unfortunately, their examples wrap, too. I'll have to try to find some of the pages where I've seen non-wrapping code blocks, and refer specifically to those. I'll be back...

Edit: I'm back. I found an example non-wrapping code block (look for the blue rectangle with code in it) at the bottom of [this]("https://help.ubuntu.com/7.04/basic-commands/C/ar01s03.html") page. What's the wiki-formatting to get that kind of rendered output?

---

### Post by Seisen on 2007-08-02
It shoudl look like this
```
{{{
text
}}}
```

Also if you have a list like this
```
1.
2.
3.
4.

```
you need to move these```
{{{
``` so they are underneath the text that you wrote.

---

### Post by Jamie Jackson on 2007-08-02
Seisen,

Thanks for the reply, but it seems you might have missed my original post, which is about {{{This Syntax}}} wrapping inappropriately. It makes [my tutorial's]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff") code blocks wrap if you narrow the browser window. This wrapping is disastrous for people copying/pasting the commands from a narrow browser window.

Thanks,
Jamie

---

### Post by nitro_n2o on 2007-08-02
sounds like a promising tutorial 
you can also post it in the HOW TO's forum

---

