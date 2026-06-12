---
title: "edit a document from a shell sript"
date: 2008-02-16
forum: General Help
---

### Post by jman12321 on 2008-02-16
How would I go about editing a file (i.e. sources.list) in a shell script, so that I can have a script edit my repositories automatically.  I want something that i can execute, and not have to give it further input.

---

### Post by lloyd_b on 2008-02-16
> **jman12321 said:**
> How would I go about editing a file (i.e. sources.list) in a shell script, so that I can have a script edit my repositories automatically.  I want something that i can execute, and not have to give it further input.

There are programs such as 'sed' and 'awk' which can be used for this purpose, but frankly I don't understand why you would need such.  If you want to maintain 2 or 3 different versions of "sources.list", then just have "sources.list.1", "sources.list.2", "sources.list.3", and copy the appropriate one over top of "sources.list".  You can have a shell script to do the copying, so that all you'd have to do is type "sudo sources 1" or "sudo sources 2".

Lloyd B.

---

### Post by ghostdog74 on 2008-02-16
> **jman12321 said:**
> How would I go about editing a file (i.e. sources.list) in a shell script, so that I can have a script edit my repositories automatically.  I want something that i can execute, and not have to give it further input.

show a sample input sources.list file, and your expected output.

---

### Post by Zwack on 2008-02-16
To answer your question....

Sed or awk, or in some cases you can get away with judicious use of grep, echo and cat....

But...

Whether these are the right tools for you depend on your planned uses...

As an aside, and it's not intended to be rude to anyone although it might come across that way....
Why is it that I've seen a lot of posts that say "How would I do some vague idea" when there are multiple ways of achieving it depending on the intricacies of what they are trying to achieve...  In some cases we really need to see the details to know if X or Y will work best.

Z.

---

### Post by ghostdog74 on 2008-02-16
> **Zwack said:**
> 
Why is it that I've seen a lot of posts that say "How would I do some vague idea" when there are multiple ways of achieving it depending on the intricacies of what they are trying to achieve...  In some cases we really need to see the details to know if X or Y will work best.

Z.
you have answered it yourself. in your last sentence.

---

