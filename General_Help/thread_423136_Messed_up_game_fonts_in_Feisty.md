---
title: "Messed up game fonts in Feisty"
date: 2007-04-25
forum: General Help
---

### Post by p_y_x on 2007-04-25
Hi Ive been puling my hair over this for two days now.
My problem is that the fonts in the game PlaneShift are all messed up, makes it pretty hard to play. I got this problem after upgrading to Feisty.

Ive tried all the tweaking of Planeshift files that this guide has [http://vaalnor.mine.nu/psdoc/?q=node/39](http://vaalnor.mine.nu/psdoc/?q=node/39)

None of em worked.

I have also tried to "manual upgrade" that is explained here [https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)
That seems to have worked for other people with font problems in Feisty.
But it didnt solve my Planeshift fonts problem.

and i have tried to reinstall the game....still messy fonts.

Does anyone have a qlue on how to fix this? I need my daily PlaneShift dose:)

---

### Post by Kohbo on 2007-04-30
Font multitexturing has been broken, try the following:
Open up the file Planeshift3D/data/config/r3dopengl.cfg in a text editor, and find this line:
Video.OpenGL.FontCache.UseMultiTexturing = yes
and change yes to no.

---

