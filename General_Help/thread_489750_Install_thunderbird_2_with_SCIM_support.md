---
title: "Install thunderbird 2 with SCIM support?"
date: 2007-07-01
forum: General Help
---

### Post by tak1150 on 2007-07-01
Hi,

If this has been addressed elsewhere, I'm sorry. But it does not seem like it.

How can I install Thunderbird 2.0 with SCIM support so I can write Japanses, etc for emails?

Those of you who are not aware of the issue, currently the binaries available from Mozilla (I tried 2.0.0.0 and 2.0.0.4) are not compatible with SCIM. Therefore, you have to start your T-bird like this:
```
export GTK_IM_MODULE=scim-bridge; thunderbird
```
in order to disable SCIM while t-bird runs.

I tried compiling it from the source, but t-bird seems a bit too complicated for me even though I've compiled plenty other programs before. Any help would be appreciated!

---

