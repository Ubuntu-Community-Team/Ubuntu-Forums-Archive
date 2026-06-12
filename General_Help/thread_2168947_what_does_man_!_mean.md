---
title: "what does man \!* mean?"
date: 2013-08-20
forum: General Help
---

### Post by webstuffg on 2013-08-20
I'm reading teach yourself unix 24 hours 3rd edition, page 16 to 18, and I would like someone to explain to me what does \!* do.  I read man man and it didn't help.  I believe \ means it's a string, but no idea what !* mean.

anybody can recommend a much better book for a newbie studying linux?

thanks.

---

### Post by lisati on 2013-08-20
The meaning can depend on context. Are you referring to this: ?
> alias man &#8216;man \!* | more&#8217;

---

### Post by webstuffg on 2013-08-20
Yes, but I specifically want to know how \!* work, what does it do.. I'm reading the book and it's frustrating the author doesn't explain it.  I google and read the man man page.

> **lisati said:**
> The meaning can depend on context. Are you referring to this: ?

---

### Post by lisati on 2013-08-20
I think the meaning is explained several chapters later in the book, in the "Wildcards" and "Regular expression notation" chapters, at least in the online edition I found of the book you mentioned.

When used on the command line, "*" is like a place holder which which matches anything, similar to what you might expect on the Windows command line. "\!" forces the command line to use "!" without doing any special substitution.

---

