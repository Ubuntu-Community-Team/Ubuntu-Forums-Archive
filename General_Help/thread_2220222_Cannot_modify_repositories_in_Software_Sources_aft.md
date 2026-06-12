---
title: "Cannot modify repositories in Software Sources after upgrading 13.10 &#8594; 14.04"
date: 2014-04-27
forum: General Help
---

### Post by lediableboiteux on 2014-04-27
A quick search on both Google and Ubuntu Forums returned nothing helpful, so I'm posting this, as the issue's quite annoying. (I'm guessing the section, sorry if I chose a wrong one.)  After upgrading my 13.10 installation to 14.04 I found out that I cannot modify repositories (by which i mean Other Sources) from Software Sources/Synaptic. I just click Modify &#8594; OK or Delete, nothing happens, no error messages. It worked in before upgrading.  Any hints on what might be going on? Thanks in advance.

---

### Post by ibjsb4 on 2014-04-27
Try opening software sources in terminal.

```
[COLOR=#555555][FONT=monospace]gksudo software-properties-gtk[/FONT][/COLOR]
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

And welcome to the forums :)

---

### Post by deadflowr on 2014-04-27
You can try opening the program directly.
It's name is "Software and Updates".

---

### Post by lediableboiteux on 2014-04-28
Well, I'm not sure what would that fix, but I tried the second hint before posting (by "Software Sources/Synaptic" I meant opening "Software and Updates" both separately and from Synaptic), the first one now, nothing.

Two more additions: 1. checking/unchecking checkboxes next to entries on list (under "Other Softare" tab) doesn't work either (I cannot change their state), 2. latest update of 'software-properties-gtk' from 0.92.36 to 0.92.37 didn't fix anything.

Any other hints? Maybe some permissions I should check? I'm guessing here.

---

### Post by lediableboiteux on 2014-05-03
UPDATE: Well, strange thing, it just started working out of blue. EOT I guess.

---

