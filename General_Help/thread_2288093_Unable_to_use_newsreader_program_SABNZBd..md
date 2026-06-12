---
title: "Unable to use newsreader program SABNZBd."
date: 2015-07-24
forum: General Help
---

### Post by arthur24 on 2015-07-24
I'm using Ubuntu 14.04 and I installed SABNZBd+    In regards to the topic title you might wonder why I post this question here on ubuntuforums.org.  The reason for this is because I cannot use the SABNZBd forums. I have never used SABNZBd and I'm new to Ubuntu. Thus far I didn´t have to much hassle into installing and configuring other aspects of the operating system. The reason I cannot use the SABNZBd forums is because they have quite a sophisticated captcha that promises to release a confirmation code if you properly enter the captcha, but I never get that code.  Which either means I always fail to type the captcha correctly or the registration field is broken.    In such cases they mention the webmasters e-mail adress to report registration problems, which I cannot use because the Firefox webbrowser tells me that javascript is not enabled and I theirfore can´t contact the webmaster.  Which ultimately brings me to the very problem why I wanted to post a question on the SABNZBd forums in the first place. Which is that SABNZBd also tells me that javascript is needed for "plush" to work. I have no Idea what plush is but it obviously is a necessary preqrequisite for SABNZBd to work.    I checked in firefox about:config > javascript.enabled and it is set to "true"  I do have adblockers and noscript installed on firefox and perhaps these plugins are the culprit causing these problems.  I hope somebody out here has a clue to solving this problem, especially as this question is better answered on the SABNZBd forums. But since I can´t complete their registration or contact their webmasters supposedly due to javascript not functioning I hope you understand.  OFFTOPIC: I use "enter" to make subsections for my text but when I "save changes" it welds all the text into a wall? Why is this?

---

### Post by howefield on 2015-07-24
> **arthur24 said:**
> ...  I do have adblockers and noscript installed on firefox and perhaps these plugins are the culprit causing these problems.  I hope somebody out here has a clue to solving this problem, especially as this question is better answered on the SABNZBd forums....

Noscript is probably blocking elements of the page, have you tried using the "temporarily allow" noscript option to selectively allow what it is blocking.

---

### Post by arthur24 on 2015-07-24
Oh my gosh, I feel pretty stupid now. I basically answered my own question.

I allowed scripts for both the SABNZBd forums registration screen and SABNZBd itself. 
SABNZBd is working now and I got a working captcha on the forums registration field.

I just recently installed NOscript and didn´t realize I have to manually allow for individual webpages.

EDIT: It also solved the subsection issue :p

---

### Post by howefield on 2015-07-24
If I recall correctly, temporarily allowing will allow for that browsing session while standard allow will allow every browsing session.

---

### Post by arthur24 on 2015-07-24
Thanks, I focused on the different noscript settings myself and concluded the same.

---

