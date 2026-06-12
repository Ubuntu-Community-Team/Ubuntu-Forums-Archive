---
title: "&quot;operation not permited&quot; while copying... (how do I copy based on MIME type?)"
date: 2006-12-15
forum: General Help
---

### Post by spudley on 2006-12-15
I have about 8000 PNG files to copy from my Ubuntu machine (Edgy) to my a drive W2K server.  I also tried copying to my 2Gb USB stick and my LInux NAS box - same problems exist.

What happens, is the copy stops - same spots - with Error "Operation not permitted" while copying "/home/spudley/..._01.png".  (and the filename changes accordingly) (I'm using Nautilus 2.14.3)

It turns out that the files that will not copy are 'shortcuts' to the same file in different directories - all nested in the one I want to copy.  Is there a way that I can bypass this error and not copy the shortcuts but only the 'real' PNG files?  The shortcut files do still have the .PNG extension - but viewing properties it says the MIME type is "shortcut to PNG image"  instead of "PNG image"

I thought about using the CLI and CP, but can I copy based only on the MIME type??

Thanks for any tips on this one!

---

