---
title: "grub issues"
date: 2013-05-17
forum: General Help
---

### Post by Cool Javelin on 2013-05-17
I just installed 12.04.2 server (no x, no graphics), and the video comes up in a mode the monitor can't handle. 

I uncommented the line GRUB_TERMINAL=console and I can now see things. I did not uncomment the GRUB_GFXMODE=1024×768.

It seems to me the two are mutually exclusive. Either it is in a text mode or it is in a graphics mode. Am I missing something?

I would like to put the monitor in a 80x50 (or 80x43) TEXT mode, but could not find any info on these choices.

Is the only choice to put it in a graphics mode like 800x600 or 1024x768 then hope for the best?

I was under the impression there were TEXT modes I could select (80x25, 80x43, 80x50 even a 132x50 mode etc...). which are different then graphics modes.

Thanks for your help.

Mark.

PS sorry my thoughts may appear a bit scrambled, it comes from banging my head against the wall too much :)

---

### Post by oldfred on 2013-05-18
You should just be able to boot to text mode.

For a one time test use e on grub menu and on linux line:
 Arrow right to where it says "quiet splash"
Replace that text with "--verbose text" without quotes

You then can edit grub to make permanent or add a separate boot stanza to grub in 40_custom if you just want it sometimes.

Video is not lines to display but pixels. So I think 640x480 may give you want you want, if monitor supports that.

---

