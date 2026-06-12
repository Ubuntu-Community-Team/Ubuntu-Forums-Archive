---
title: "Electronics schematic CAD tools"
date: 2020-02-27
forum: General Help
---

### Post by Nina_W on 2020-02-27
I'm looking for a CAD tool for doing electronics schematics. I've tried KiCAD and Oregano and both seem to have the same flaw. If you place two components and put a wire between them it registers that the wire is connected (I can generate a netlist) but if I try to move a component the wire connection doesn't move. This isn't a huge problem with discreet components but is once you get to ICs.

Are there any CAD tools out there that move the wires with any component they're connected to?

I don't need much else in terms of functionality, I don't need any simulation and I can do without circuit layout, although layout would be good to have.

---

### Post by HermanAB on 2020-02-27
There is a way to do that with KiCAD, but I can't remember the details - don't use it often enough.  I believe Move and Drag are handled differently.  Look for a tutorial.

---

### Post by Nina_W on 2020-02-29
Thanks, I can see tutorials telling you how to do this for PCB layouts but nothing for schematics (ie. circuit diagram). Can you clarify that it was the schematic section where you did this? If so I'll try to figure it out but I don't want to waste any more time if it is something that can't be done.

---

### Post by him610 on 2020-02-29
Searched on this term in my browser, *linux electrical circuit cad software*
Comes up with a whole page of leads. Here is one of them, [https://www.ghacks.net/2011/02/17/electric-cad-program-on-linux/]("https://www.ghacks.net/2011/02/17/electric-cad-program-on-linux/")
Hope you find what you are looking for.

---

### Post by HermanAB on 2020-03-01
It should be as simple as Ctrl Click Drag.  Google for “KiCad drag with rubber banding”.

---

### Post by Nina_W on 2020-03-01
Many thanks! That's it. Select the pointer, Ctrl click on component and drag. It doesn't re-route the wires so they look tidy, but I find best to do that manually anyway.

---

### Post by HermanAB on 2020-03-16
If the wires end up skew, try to drag the corner points.  If that fails on some points, delete and redo the messed up wires.

One can also drag multiple components at the same time.  The wires between these parts will remain OK, the outside wires may get messed up a bit, but I haven't found it to be a big problem.

---

