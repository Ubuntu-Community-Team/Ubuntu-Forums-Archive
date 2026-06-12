---
title: "How can I make my bars totally hide?"
date: 2006-12-12
forum: General Help
---

### Post by jincast90 on 2006-12-12
Hello. I like to set my bars to automaticly hide when I am not hovering my mouse over them. I was just thinking today that It would be cool if the bars would be not visible at all, instead of having a few pixels pocking up. Can anyone tell me how to make them totally disapeer so not even a few pixels are shown when not hovering your mouse over them?

Thanks.

---

### Post by bswilson on 2006-12-12
Close your eyes, and they'll totally disappear.  ;) 

Not really sure what "bars" you're talking about.  I assume you mean the Gnome panels that appear at the top and bottom of the screen?

---

### Post by jincast90 on 2006-12-12
> **bswilson said:**
> I assume you mean the Gnome panels that appear at the top and bottom of the screen?

You are right :D

---

### Post by jincast90 on 2006-12-13
Bump.. Anyone know?

---

### Post by strabes on 2006-12-13
There's an option in gconf-editor. Go to apps -> panel

I'm in windows right now so I can't check specifically but I remember looking for this same thing. The option is something like "Panel hide size." I'm not exactly sure. I AM sure that the option is in gconf-editor somewhere though.

---

### Post by mcduck on 2006-12-13
the setting is in apps/panel/toplevels/(your panel name here)/auto_hide_size.

Just set that to 1 and you'll hardly see your panel any more. (0 doesn't work, because you still need to be able to move mouse over the panel to make panel unhide. you can set it to 0 but it has same effect as 1)

---

### Post by jincast90 on 2006-12-15
> **mcduck said:**
> the setting is in apps/panel/toplevels/(your panel name here)/auto_hide_size.

What? Can you please explain to me again where the setting is located.. Where is apps for example.

---

### Post by mcduck on 2006-12-15
> **jincast90 said:**
> What? Can you please explain to me again where the setting is located.. Where is apps for example.

I was just elaborating to the previous post.. I didn't notice that there wasn't actually instructions for opening gconf-editor ;)

Press alt-F2 and run 'gconf-editor' to open Configuration Editor.

---

### Post by Eddy Dean on 2006-12-15
You could also just kill the process named gnome-panel... But then what's the point of using Gnome?

---

### Post by mcduck on 2006-12-15
> **Eddy Dean said:**
> You could also just kill the process named gnome-panel... But then what's the point of using Gnome?

that doesn't work, panels would just autospawn back :)

---

### Post by jincast90 on 2006-12-15
Allright.. It worked.. Thanks alot..

---

### Post by bobosity on 2006-12-15
Right click on the panel and choose properties. Just check every box there.

---

### Post by jincast90 on 2006-12-16
Nvm

---

### Post by floke on 2006-12-22
Just looked for this myself and found the answer from a different site - so can claim no credit for it....

To completely hide panels:
(1) Open terminal and run 'gconf-editor'
(2) The path you need is apps/panel/toplevels/top_panel
(3) Change the entry for 'auto_hide_size' from 6 to 0 

One of the posts above said that 0 didn't work, or that it was the same as 1 - I don't know about the 'same as 1' bit - but have set mine to 0 and now my panel is completely hidden :-D 

(Actually there is the thinnest of thin lines at the top - so maybe that's what the '1' bit is!)

Cheers

---

