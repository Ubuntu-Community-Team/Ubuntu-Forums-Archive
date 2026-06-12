---
title: "Cannot install inkcut as an extension in inkscape"
date: 2023-07-19
forum: General Help
---

### Post by grey1beard on 2023-07-19
I'm running ubuntu 22.04, with inkscape 0.92. 
I've recently bought a Bosscut Gazelle cutter, and installed inkcut as a standalone program, which I can launch from Terminal.
Having begun to learn how to use it, I should like to install it as an extension in inkscape.
Much research later, I have extracted the files in incut-for-inkscape-2.1.1.tar.gz into the .config/inkscape/extensions folder, and restarted inkscape, all as found here, in the forum.
However, the extension doesn't appear.
MTIA for any guidance.
John

---

### Post by MAFoElffen on 2023-07-20
That doesn't exactly sound like you followed InkCut's own tutorials: 
[https://www.codelv.com/projects/inkcut/docs/installing](https://www.codelv.com/projects/inkcut/docs/installing)
 [https://github.com/inkcut/inkcut/blob/master/docs/tutorial.md](https://github.com/inkcut/inkcut/blob/master/docs/tutorial.md)

---

### Post by grey1beard on 2023-07-20
Thanks.
However, I did use the first of your links to install inkcut, and it currently works.
I followed the link at the bottom of their page where it gives > Download the extension files from Inkcut's extension page from the Inkscape extension list .
As far as I can see, and I have looked at all the links and options, I just get sent round in circles.
The posts of other people who have had the same problem, gave the course of action that I have followed, but in my case, I seem to have fallen at the last fence.
Perhaps I should have the files inside the inkcut folder ?
John

---

### Post by MAFoElffen on 2023-07-20
Yes. Those are the inkscape extensions for inkcut...

For example, this is the extension define (inkcut_open.inx)
```

<inkscape-extension>
  <_name>Open current document...</_name>
  <id>org.ekips.filter.inkcut.open</id>
  <dependency type="executable" location="extensions">[COLOR=#ff0000]inkcut_open.py[/COLOR]</dependency>
  <dependency type="executable" location="extensions">[COLOR=#ff0000]inkcut4inkscape.py[/COLOR]</dependency>
  <effect>
    <object-type>all</object-type>
    <effects-menu>
       <submenu _name="Inkcut"/>
    </effects-menu>
  </effect>
  <script>
    <command reldir="extensions" interpreter="python">[COLOR=#ff0000]inkcut_open.py[/COLOR]</command>
  </script>
</inkscape-extension>

```
So yes, all those files...

---

### Post by grey1beard on 2023-07-21
I've moved the files in the screen shot above, into the inkcut folder shown, then rebooted, but nothing shows in the Extensions drop down menu to show that it is available.
However the message below did appear. Unfortunately it's well outside my knowledge level to understand what it means, so unable to move forward.
John

---

### Post by grey1beard on 2023-07-30
Now close to giving up. 
I've tried installing a virtual box to run windows 10, which I believe inkcut works in, but every turn I take, (I've tried Oracal VM , Gnome boxes, and Open-VM) seems to run into a brick wall.
Now trying KVM, but still an unexpected result.

---

