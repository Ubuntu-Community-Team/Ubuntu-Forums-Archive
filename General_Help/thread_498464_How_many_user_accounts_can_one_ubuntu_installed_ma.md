---
title: "How many user accounts can one ubuntu installed machine have?"
date: 2007-07-11
forum: General Help
---

### Post by McLaughysSN on 2007-07-11
Hey guys, just have a couple of questions for a school project.

1. How many user accounts can one ubuntu desktop installed machine support?

2. How many computer devices can it support?

not sure how to answer these as vague as they are. Is there a numerical answer?

Thanks

---

### Post by mbeierl on 2007-07-11
User accounts?  Unix is used in corporations, and the underlying authentication mechanism is applicable across the board.

I don't know of a hard number, but it should support as many as there are uids, which I think is 65535.

---

### Post by McLaughysSN on 2007-07-11
Thanks a million my friend, that works.

---

### Post by mbeierl on 2007-07-11
Just realized - what do you mean by devices?  As in keyboard, mouse, etc?  The limit is usually that computer's hardware, not the OS for that sort of thing.

---

