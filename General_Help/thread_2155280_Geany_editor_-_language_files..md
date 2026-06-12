---
title: "Geany editor - language files."
date: 2013-06-17
forum: General Help
---

### Post by Sector11 on 2013-06-17
For [gedit]("http://conky.pitstop.free.fr/wiki/index.php5?title=Gedit_and_Conky_%28en%29") and [medit]("http://conky.pitstop.free.fr/wiki/index.php5?title=Medit_and_Conky_%28en%29") there is a language file available for "conky".

Does anyone know how to do this with geany? For all the searching I have done all I can find is "themes" ... that's not what I'm looking for.

---

### Post by falldown on 2013-06-17
I do know that Geany will colorize the syntax as long as the conky file is labeled as conkyrc, 
but I do not know how to get the same result with any of my oddly named conky files.

---

### Post by Sector11 on 2013-06-17
> **falldown said:**
> I do know that Geany will colorize the syntax as long as the conky file is labeled as conkyrc, 
but I do not know how to get the same result with any of my oddly named conky files.

That's because it is recognizing the conky**rc** ending as a *config* file, but it's not the same.

The conky.lang file is specific to a file that has *conky* anywhere in the name --- or on the first line of the conky file, I think:

```
<language id="conkyrc" _name="Conky" version="2.0" _section="Others">
  <metadata>
<!--    <property name="mimetypes">text/plain</property> -->
    <property name="globs">*conky*</property>
    <property name="line-comment-start">#</property>
  </metadata>
```

and it looks different:
[CENTER][[img]http://s20.postimg.org/mme5834ax/2013_06_18_00_04_16_1920x1080_Sector11.jpg[/img]](http://postimg.org/image/mme5834ax/)[/CENTER]

If you renamed your conkys to "oddly_named_conky**.rc**" they will always be considered a "config file" by geany.
[CENTER][[img]http://s20.postimg.org/6pfdbdbwp/2013_06_18_00_14_25_1920x1080_Sector11.jpg[/img]](http://postimg.org/image/6pfdbdbwp/)[/CENTER]

**conky.lang** - for medit and gedit can be downloaded from the links in the first post.

If anyone knows how to do this I'm willing to try and convert it to a working solution for geany but I don't know how.

---

