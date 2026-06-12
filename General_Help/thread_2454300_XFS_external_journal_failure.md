---
title: "XFS external journal failure"
date: 2020-11-26
forum: General Help
---

### Post by clarknova on 2020-11-26
I've done lots of searching and reading, but haven't been able to find any documentation on this scenario. If I create an XFS volume and use an external journalling device, and that journal device should fail, what is the result?

[LIST=1]
[*]Does the volume freeze?
[*]Does it revert to read-only?
[*]Can I just replace the journal device and carry on?
[*]Do I lose everything on the volume?
[*]Other?
[/LIST]

Thanks.

---

### Post by HermanAB on 2020-11-27
Why don't you just run a test?

---

