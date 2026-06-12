---
title: "bash autocomplete; less is more?"
date: 2007-12-16
forum: General Help
---

### Post by yurimxpxman on 2007-12-16
Is there a way to make bash's auto-complete feature to use less instead of more?

---

### Post by matthewcraig on 2007-12-16
Can you elaborate on your question?  I was not aware auto-complete (the tab feature, right?) used either.

---

### Post by yurimxpxman on 2007-12-19
> **matthewcraig said:**
> Can you elaborate on your question?  I was not aware auto-complete (the tab feature, right?) used either.

If there's more than can be displayed on screen, it uses more.

---

### Post by yurimxpxman on 2008-01-03
Bump!

Any ideas?

---

### Post by p_quarles on 2008-01-03
> **yurimxpxman said:**
> Bump!

Any ideas?
Can you go into a bit more detail? A screenshot, perhaps? I just tried this out, and Bash most certainly does *not* use a pager with tab-completion unless you specifically invoke one.

---

### Post by PeterJS on 2008-01-03
> **p_quarles said:**
> Can you go into a bit more detail? A screenshot, perhaps? I just tried this out, and Bash most certainly does *not* use a pager with tab-completion unless you specifically invoke one.


Yes it does, pop open a terminal and type 'a [tab]' , it will ask you if you want to display all 100+ possible completions, if you say yes it will pipe the output through more, which I had never thought about before seeing this thread, but now that it's been brought up it would be nice to have it use less instead of more.

It's a terrible hackish solution, and maybe someone wiser will come by and tell me this is a terrible idea, but how about just renaming the more binary to something like more.back, and then symlinking in less.

---

### Post by p_quarles on 2008-01-03
@PeterJS: Okay, I see now. I guess I've never bothered with the "see all possible completions" part before.

---

### Post by yurimxpxman on 2008-01-10
> **PeterJS said:**
> Yes it does, pop open a terminal and type 'a [tab]' , it will ask you if you want to display all 100+ possible completions, if you say yes it will pipe the output through more, which I had never thought about before seeing this thread, but now that it's been brought up it would be nice to have it use less instead of more.

It's a terrible hackish solution, and maybe someone wiser will come by and tell me this is a terrible idea, but how about just renaming the more binary to something like more.back, and then symlinking in less.

nah, that doesn't work :( The scrolling functionality must be built into bash.

---

### Post by meme32 on 2008-01-21
> **p_quarles said:**
> Can you go into a bit more detail? A screenshot, perhaps? I just tried this out, and Bash most certainly does *not* use a pager with tab-completion unless you specifically invoke one.

Wrong... it does too... (or it can depending on your version of bash) 
Right from the man page:
     page-completions (On)
          If set to On, readline uses an internal more-like pager
          to  display  a  screenful  of possible completions at a
          time.

To the OP check the man page for the page-completion option.   You should be able to fiddle with the various bash **page-completion** options to tweak it how you like it.  

Sometimes those options are often defaulted to something which we're not used to which confuses thing, especially when the option look like a standard program.  The page completion option looks like more, but it's not.  It's also not possible to tell bash to use less internally.  You have to use  standard pipe to get it in to less (which is probably what you were looking for in the first place).

You should be able to add a "set page-completion=off" to whatever you want for your start up files, bashrc or profile or whatever.

I'm sure my syntax is off a bit.  The man page and this will help more.  [https://wiki.ubuntu.com/Spec/EnhancedBash](https://wiki.ubuntu.com/Spec/EnhancedBash)

Hope that helps.

---

