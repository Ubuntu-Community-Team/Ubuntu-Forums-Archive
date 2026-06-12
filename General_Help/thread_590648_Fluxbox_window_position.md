---
title: "Fluxbox window position"
date: 2007-10-24
forum: General Help
---

### Post by PurposeOfReason on 2007-10-24
Is there a way to control what coordinates a window is opened at? When I move a window, in the center a x,y number list comes up where the window is based off of it's top left corner and I'd like for everything to start at a certain point. I found "session.screen0.windowPlacement:	RowSmartPlacement" in the init and was wondering if that could do it.

---

### Post by mojoman on 2007-10-25
Could devilspie be what you're looking for? It's in the repositories. I haven't used it myself but stumbled on it when I tried to get on top of metacity's annoying behavior with twinview.

/mojoman

---

### Post by cknight on 2007-10-25
This is relatively easy with no editing of configuration files or third party apps required.  Simply right click on the title bar, go down to 'Remember' and enable 'Position' (or is it 'Placement'? not sure the exact option as I'm at work at the moment).  I think you need to choose 'Save on Close' too. This automatically updates your apps file with the current position of the window.  Then whenever this application is opend it will be opend at the previously closed position. 

Other options allow for remembering dimensions and workspace too among others.

---

### Post by mojoman on 2007-10-25
> **cknight said:**
> This is relatively easy with no editing of configuration files or third party apps required.  Simply right click on the title bar, go down to 'Remember' and enable 'Position' (or is it 'Placement'? not sure the exact option as I'm at work at the moment).  I think you need to choose 'Save on Close' too. This automatically updates your apps file with the current position of the window.  Then whenever this application is opend it will be opend at the previously closed position. 

Other options allow for remembering dimensions and workspace too among others.

:oops: (My brain ceased to function when I replied and for some reason I was thinking about other window managers. I use fluxbox myself so it's amazing that I managed to give such a faulty answer. Sorry.)

---

### Post by PurposeOfReason on 2007-10-25
Thanks. That's actually just what I was looking for. I keep my conky on the left so I like my windows on the right. No, it is not possible to switch those around. Too used to it. lol

---

### Post by jviscosi on 2007-10-25
> **mojoman said:**
> :oops: (My brain ceased to function when I replied and for some reason I was thinking about other window managers. I use fluxbox myself so it's amazing that I managed to give such a faulty answer. Sorry.)

Don't feel bad, the devilspie suggestion isn't **that** faulty ... you can use it with wildcards to make its rules apply to any window that you open, including ones that Fluxbox has never seen before and that hence don't have any position information set for them.  I'm not sure if you can wildcard the Flux "apps" file in such a fashion.

---

### Post by cknight on 2007-10-26
The fluxbox apps file supports wildcard/regular expressions and even limits the number of times the apps formatting is applied. This can be used to group similiar apps:

```
[app] (.*[tT]erm) {2}
```

would match the first two applications ending in 'term' or 'Term' (e.g. aterm, xterm, eterm, etc...).  Properties could be grouped too, with multiple [app] definitions applied to one set of properties.  And of course, I think the following would work:

```
[app] (.*) 
```

which would match any app opened.  Not sure the order of parsing and if this should go at the start or end of the apps file as this has the potential to override any previous setting.  But, as you can see, the apps file is really powerful for specifying where and how any window should appear.

For more info, check out [editing the apps file on the fluxbox wiki]("http://fluxbox-wiki.org/index.php/Howto_edit_the_apps_file")

---

