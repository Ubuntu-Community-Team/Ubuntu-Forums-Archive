---
title: "Text codes for characters in compose combos (e.g. &lt;quotedbl&gt;, &lt;comma&gt;, &lt;space&gt; etc.)"
date: 2015-03-24
forum: General Help
---

### Post by Stannis_King on 2015-03-24
I want to set up some compose key sequences in .XCompose, but I don't know what are the codes for characters I want to be parts of the sequence.

These are some lines from the file in question:

```
<dead_tilde> <space>                 : "~"   asciitilde # TILDE
<dead_tilde> <dead_tilde>            : "~"   asciitilde # TILDE
<dead_acute> <space>                 : "'"   apostrophe # APOSTROPHE
<dead_acute> <dead_acute>            : "´"   acute # ACUTE ACCENT
<Multi_key> <apostrophe> <apostrophe>     : "´"   acute # ACUTE ACCENT
```

I want to set up a compose sequence that takes in two cyrillic characters, but if I just put the cyrillic characters themselves (e.g. <Multi_key> <&#1073;> <&#1084;>), it doesn't work. Where can I find a complete list of these "codes", including the "codes" for cyrillic characters?

---

