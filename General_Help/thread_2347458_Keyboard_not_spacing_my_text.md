---
title: "Keyboard not spacing my text"
date: 2016-12-25
forum: General Help
---

### Post by RobGoss on 2016-12-25
Hello everyone I've been having issues using my key board when replying to comments here on the forum, when I attempt to try answering comments as I'm writing I cannot not space the text only if I scroll down to the bottom of the post can I space my text in a comment 

This mostly happens when I try responding to a post using **reply with quote,** I'm using **Dell inspiron -531** Ubuntu 16.04.1 Xenial Xerus,  my machines are fairly new so I know it's not a hardware issue

Oh and I have this issue on a number of my machine I just tried it with Linux Mint and the same problem

Any help would be appreciated

---

### Post by Keith_Helms on 2016-12-25
> **RobGoss said:**
> Hello everyone I've been having issues using my key board when replying to comments here on the forum, when I attempt to try answering comments as I'm writing I cannot not space the text only if I scroll down to the bottom of the post can I space my text in a comment 

This mostly happens when I try responding to a post using **reply with quote,** I'm using **Dell inspiron -531** Ubuntu 16.04.1 Xenial Xerus,  my machines are fairly new so I know it's not a hardware issue

Oh and I have this issue on a number of my machine I just tried it with Linux Mint and the same problem

Any help would be appreciated

What do you mean by "spacing your text"?  Do you mean putting multiple spaces between words?  Putting blank lines between paragraphs?  Something else?

---

### Post by RobGoss on 2016-12-25
When ever I type it will not space the text, example

Let's say I'm writing Welcome to the forum

It types like this, Welcometotheforum it types it altogether
 
It's strange but yet it's happening

---

### Post by sudodus on 2016-12-25
It could be another way that the system running the Ubuntu Forums is playing tricks on us.

PleaseReportItAtTheFollowingLink :-P

[Do you want to help us debug the posting issues ?](https://ubuntuforums.org/showthread.php?t=2331266)

---

### Post by RobGoss on 2016-12-25
Yes Sudoduo I think you might be right this has been like this for a while now I tried not to let it bother me but it's does not allow me to reply with a quote unless I use the quote tags

Do I just post about this issue from the link you posted?

I'll use that link you provided thanks a bunch

---

### Post by sudodus on 2016-12-25
Yes, and enter the time it occurred like this:

```
date -u
sön 25 dec 2016 22:05:01 UTC
```

You can add that it happens all the time, but anyway, I think they want the date for a 'verified incident'.

---

### Post by RobGoss on 2016-12-25
Thanks so much Sududo will do

---

### Post by &amp;KyT$0P# on 2016-12-25
sudodus, are other people seeing this same misbehavior on these forums?

RobGoss, what browser(s) (& versions) are you using?  What extension(s) do you have in your browser?

---

### Post by wildmanne39 on 2016-12-25
I do not believe that is one of the forum issues we are having.

---

### Post by sudodus on 2016-12-26
I am guessing, I don't know but I can expect 'anything' from this software after a very long time with problems. What I know is that our forums are more tricky from the advanced editor (which is started by replying with quote as described in the opening post) than from the simple editor.

---

### Post by RobGoss on 2016-12-26
> RobGoss, what browser(s) (& versions) are you using? What extension(s) do you have in your browser?

I'm using the following build

**Google chrome:** 55.0.2883.87 (Official Build) (64-bit)

As far as extensions are concerned I don't really use many I have about** 6 - total,** listed as the following

Addthis,  Checker for Gplus,  Google notifications,  Push bullet,  Popchrom,  Reply for Google,

The Popchrom is disabled after moving over to Linux full time it no longer works

The only way I was able to quote **Halogen2 **in this thread is to go all the way down to the last post click on Quote then go back to his post and copy the text and paste it

I use Google chrome on all my machine noting more, a total of 8 machines. I never had any issues but a few months ago I notice this strange  **behavior **and have been meaning to bring it to the forums attention 

All my machines are **64-bit **and all are up to dateso I do not believe this has anything to do with my machines. If it happen on only **one machine **and not the others then I would say yea maybe it's something that going on with that machine but not all  

Thanks so much guys very much appreciated

---

### Post by vasa1 on 2016-12-26
> **RobGoss said:**
>  ...I have about** 6 - total,** ...

No ad blocker? No script blocker? Are you allowing or blocking javascript? What happens with a new, clean profile?

---

### Post by RobGoss on 2016-12-26
> What happens with a new, clean profile?

Not sure what you mean by this, I don't use any ad blockers of any sort or script blockers

---

### Post by vasa1 on 2016-12-26
> **RobGoss said:**
> Not sure what you mean by this, ...
Read support.google.com/chrome/bin/answer.py?hl=en&answer=142059 and [https://support.google.com/chrome/answer/2364824](https://support.google.com/chrome/answer/2364824)

---

### Post by jeremy31 on 2016-12-26
> **sudodus said:**
> I am guessing, I don't know but I can expect 'anything' from this software after a very long time with problems. What I know is that our forums are more tricky from the advanced editor (which is started by replying with quote as described in the opening post) than from the simple editor.

I just tested this and using the enhanced editor setting with chrome disables spaces somehow using Reply with quote
[https://ubuntuforums.org/profile.php?do=editoptions](https://ubuntuforums.org/profile.php?do=editoptions)  See Miscellaneous Options near the bottom of the page to switch to the Standard editor

---

### Post by vasa1 on 2016-12-26
> **jeremy31 said:**
> I just tested this and using the enhanced editor setting with chrome disables spaces somehow using Reply with quote
[https://ubuntuforums.org/profile.php?do=editoptions](https://ubuntuforums.org/profile.php?do=editoptions)  See Miscellaneous Options near the bottom of the page to switch to the Standard editor
That looks like a winner. I don't use the advanced editor mode, ever. I've read it can cause unpredictable issues or something like that.

I can confirm what jeremy31 wrote. This caution is worth quoting:> When posting messages to the forums or other members, there are three interface types available to you. The simplest of these is a simple text box, while the last is a fully-fledged WYSIWYG editor, which allows you to format your text as you want it and see the results immediately.

Depending upon the capabilities of your web browser, you may not be able to use all of these options. If you experience problems when posting messages, try switching to a different interface type.

Please be warned that if you use BBCode in WYSIWYG mode, it is easy to misplace edits within already typed BBCode and thus cause unwanted formatting effects. If you use BBCode you may find that either the Basic or Standard interface suits your purposes better.

---

### Post by jeremy31 on 2016-12-26
> **vasa1 said:**
> That looks like a winner. I don't use the advanced editor mode, ever. I've read it can cause unpredictable issues or something like that.

Seems to be a bug in VB4 with the enhanced editor as I tried the same in another forum that uses VB4

Firefox seems to work fine though

---

### Post by vasa1 on 2016-12-26
> **jeremy31 said:**
> Seems to be a bug in VB4 with the enhanced editor as I tried the same in another forum that uses VB4

Firefox seems to work fine thoughVivaldi snapshot behaves like Chrome. Anyway, because of that caution, I don't use enhanced mode.

---

### Post by RobGoss on 2016-12-26
> **jeremy31 said:**
> I just tested this and using the enhanced editor setting with chrome disables spaces somehow using Reply with quote
[https://ubuntuforums.org/profile.php?do=editoptions](https://ubuntuforums.org/profile.php?do=editoptions)  See Miscellaneous Options near the bottom of the page to switch to the Standard editor


This is a test to confirm Jeremy findings BAM :P

---

### Post by RobGoss on 2016-12-26
> **jeremy31 said:**
> Seems to be a bug in VB4 with the enhanced editor as I tried the same in another forum that uses VB4

Firefox seems to work fine though


I think you are correct **Jeremy**, I changed the settings from Enhanced to Standard and it seems to work

Thank you brother for picking that up it's been driving me crazy 8-[

Well it seems to be working now and I wanted to thank you guys for all the afford great gorup

---

### Post by mgarrett682 on 2016-12-26
If I try to "reply with quote" I get the same issue. The only way I can get a space between words is to type several and when they get underlined for misspelling I can then back up and hit the space bar to enter a space between words. It only happens if I select "reply with quote," otherwise the space bar works fine.

---

### Post by sudodus on 2016-12-26
> **RobGoss said:**
> I think you are correct **Jeremy**, I changed the settings from Enhanced to Standard and it seems to work

Thank you brother for picking that up it's been driving me crazy 8-[

Well it seems to be working now and I wanted to thank you guys for all the afford great gorup

Thanks for bringing this problems to our attention, RobGoss, and thanks for finding the solution, Jeremy :-)

---

### Post by RobGoss on 2016-12-26
You are most welcome I will mark this as solved

---

