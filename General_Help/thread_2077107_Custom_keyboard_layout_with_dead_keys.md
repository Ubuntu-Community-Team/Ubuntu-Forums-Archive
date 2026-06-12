---
title: "Custom keyboard layout with dead keys"
date: 2012-10-27
forum: General Help
---

### Post by UTF16 on 2012-10-27
I’m looking for a way to make the same custom keyboard layout I use in Windows which I created using a program called "Microsoft keyboard layout creator". It’s a formidable tool that allows to assign any character to any key combination. It generates a package you can install on any Windows machine.

On the other hand, as far as I can tell, there is no such tool for Linux. Numerous tutorials on the net state that one has to modify a "symbols" file in /usr/share/X11/xkb folder of a particular language. As simple as that. Except that none of these tutorials mention how to define a desired dead key.

A dead key is a key that do not produce any character when pressed, but modifies the next one. For example, using my personal keyboard layout, pressing a dead key and then the Latin letter [g] produces the character [&#603;]. Moreover, pressing the same dead key and a 4 level character [&#613;], produces the character [&#649;]. I need to define some 200 of such sequences.

So how do I do that?

---

