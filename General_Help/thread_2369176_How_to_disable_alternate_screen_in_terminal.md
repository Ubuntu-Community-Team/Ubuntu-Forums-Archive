---
title: "How to disable alternate screen in terminal"
date: 2017-08-19
forum: General Help
---

### Post by daryl9 on 2017-08-19
I'm a command line user.  I use the terminal a lot and run most things from the command line.  One frustration that I have is whenever I use less, or read a man page, the text disappears after I close whatever it was that I was reading.  How do I disable that?

Thanks

Daryl

---

### Post by deadflowr on 2017-08-19
Not sure there's a one-shot one size fits all answer to that.
But you can use -X (or --no-init) with less.
And you can use the pager option with man.
like so,
```
 less -X file
man --pager=pager-name-here manpage
```
I used more as the pager and it did what you wanted.
fwiw

---

### Post by daryl9 on 2017-08-20
> **deadflowr said:**
> Not sure there's a one-shot one size fits all answer to that.
But you can use -X (or --no-init) with less.
And you can use the pager option with man.
like so,
```
 less -X file
man --pager=pager-name-here manpage
```
I used more as the pager and it did what you wanted.
fwiw

Thank for the suggestions.  

I was hoping for a setting in the terminal, or pass a parameter when starting the terminal.  But, these work, so I'll make do.

Thank you again for the suggestions.

Daryl

---

