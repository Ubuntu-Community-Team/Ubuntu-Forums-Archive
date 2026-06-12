---
title: "Force empty Rubbish Bin?"
date: 2013-10-11
forum: General Help
---

### Post by juanfernandes on 2013-10-11
Hi All,

Is there another way to force the Rubbish Bin to empty? 

There are 2 folders in there, which I don't know what they were when I deleted them from my home folder. 

I have tried: [COLOR=#333333][FONT=Ubuntu]sudo rm -rf ~/.local/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]share/Trash/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]files/*

But just seems to get stuck after the password is typed.

Anything else I can try? 

Its Ubuntu 13.04.

Thanks
Juan[/FONT][/COLOR]

---

### Post by VMC on 2013-10-11
What do you means by  "stuck"? Does it just come back with a prompt or hangs.
How about finding what's in there first: 'ls -la [COLOR=#333333][FONT=Ubuntu]~/.local/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]share/Trash/[/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]files/*[/FONT][/COLOR]'

---

