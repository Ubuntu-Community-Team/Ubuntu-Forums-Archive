---
title: "[Newbie] Confused with Open Source Stuffs T_T"
date: 2006-12-25
forum: General Help
---

### Post by pmcastillo on 2006-12-25
I'm new to this Open Source things...

1.) I made the program, then someone came at get my program, and RENAMED the name of my program, and redistribute it saying that its HIS work. Do I have any protection from these?

2.) What are these licenses (like the GPL)? What's the difference between giving the program with the source code, and saying, "Hey! I got a program for all of you guys, you change, edit, or do whatever you want", and the difference between having a license?

3.) What do I need to do to obtain a license? (like GPL)

---

### Post by Rippey on 2006-12-25
[http://www.gnu.org/](http://www.gnu.org/)

---

### Post by az on 2006-12-25
> **pmcastillo said:**
> I'm new to this Open Source things...

1.) I made the program, then someone came at get my program, and RENAMED the name of my program, and redistribute it saying that its HIS work. Do I have any protection from these?

2.) What are these licenses (like the GPL)? What's the difference between giving the program with the source code, and saying, "Hey! I got a program for all of you guys, you change, edit, or do whatever you want", and the difference between having a license?

3.) What do I need to do to obtain a license? (like GPL)

Good questions.  I will do my best.  I will tackle them in reverse:

3-  As an author of a work, you are granted copyright.  You sign your name to your work and you then decide to distribute it.  A licence is simply the terms under which you allow others to use your work.  So, Copyright = "this work is mine."  Licence = "this is how you can use my work."

2-  The GPL is a licence.  Something without a licence is called Public Domain.  No one really uses that.  There are restrictive licences and there are permissive ones. 

Forget about licencing for a second.

Software freedom is the concept that you should be allowed certain rights when using software.  Those rights are known a the four freedoms:

1-  The right to obtain and use the software for any purpose.
2-  The right to study the source code.
3-  The right to modify that source code.
4-  The right to redistribute the changed source code.  

In a world where computers and software are everywhere, it's probably a good idea to avoid dealing with "black boxes" and use software that is free and open.  Although you may not be able to personaly study every line of code, the fact that the software is distributed transparently is a great asset.

As well, the collaborative approach of a lot of people solving small problems and sharing their work has made the software really excellent.

Most of the developers who wrote the applications that make up Ubuntu are strong believers in software freedom.

...Back to licencing.

The GPL is the classic free-libre open source licence.  It protects your four freedoms and obliges the recipient of the code to redistribute the changes under the same licence - that way, the software is always free.

FreeBSD is a Unix operating system that is released under a BSd licence.  A BSD lience is a lot like Public Domain except that it obliges you to attribute the work to the original author and it obliges you to display the licence.  Mac OS X is a fork of freeBSD that they made proprietary.  They are not obliged to release the source so you do not have any of the four freedoms.  Had FreeBSD been licenced under the GPL, that would not be possible.

Windows is a proprietary OS.  Again, none of the four freedoms.

Vendors of proprietary software will try to tell you that free-libre software licencing is complicated.  It's actually a lot simpler than proprietary licences.  Every single proprietary licence is different.  So long as a free-libre software licence is GPL-compatible (protects your freedoms) you know where you stand.


That's it.

---

### Post by po0f on 2006-12-25
[quote=azz]... Something without a licence is called Public Domain. No one really uses that. ...[/quote]

Sorry to be nit-picky, but [SQLite does](http://www.sqlite.org/copyright.html).  From what I hear [more than a few](http://www.python.org/download/releases/2.5/highlights/) people like it.

---

### Post by pmcastillo on 2006-12-26
Okok, thanks man! Ummmmm... just one more thing...

> A BSD lience is a lot like Public Domain except that it obliges you to attribute the work to the original author and it obliges you to display the licence. Mac OS X is a fork of freeBSD that they made proprietary. They are not obliged to release the source so you do not have any of the four freedoms. Had FreeBSD been licenced under the GPL, that would not be possible.

**QUESTION NUMBER 1:** Ahhh, ok. So BSD license is better, coz the recipient must acknowledge the original author's work. And because of BSD License, no one can just "steal" somebody's work and consider them as THEIR work. **(A)** So with BSD license, I could study other source codes and apply it to my program, just ALWAYS acknowledge from where I got those source code, am I getting it right? **(B)** BTW, what's the meaning of "Mac OS X is a fork of freeBSD"? I'm quite slow at idioms :-D **PLEASE FORGVE MY INQUISITIVENESS!** :-D  : **(C)** Can I get some ideas from Open Source stuffs (but not the WHOLE source code), and apply it to my program and then sell it? Is it illegal? Or is the "Fair Use" applies? [http://en.wikipedia.org/wiki/Fair_use](http://en.wikipedia.org/wiki/Fair_use)

> In a world where computers and software are everywhere, it's probably a good idea to avoid dealing with "black boxes" and use software that is free and open. Although you may not be able to personaly study every line of code, the fact that the software is distributed transparently is a great asset.

**QUESTION NUMBER 2:**  What are "black boxes"? Are they "illegally acquired codes"?

> As an author of a work, you are granted copyright. You sign your name to your work and you then decide to distribute it. A licence is simply the terms under which you allow others to use your work. So, Copyright = "this work is mine." Licence = "this is how you can use my work."

**QUESTION NUMBER 3:** So to acquire a GPL license, I'll just say, "Hey, I decided to be a GPL, so abide the rules :)"? Or do I need to go GNU's office to acquire a license?

---

### Post by Sef on 2006-12-26
> (B) BTW, what's the meaning of "Mac OS X is a fork of freeBSD"? I'm quite slow at idioms

MACOSX is based on FreeBSD.  Hence it is a fork of FreeBSD.

> 1: Ahhh, ok. So BSD license is better, coz the recipient must acknowledge the original author's work. And because of BSD License, no one can just "steal" somebody's work and consider them as THEIR work.

The [GPL]("http://www.gnu.org/licenses/gpl-faq.html") does also:

> I want to get credit for my work. I want people to know what I wrote. Can I still get credit if I use the GPL?
    You can certainly get credit for the work. Part of releasing a program under the GPL is writing a copyright notice in your own name (assuming you are the copyright holder). The GPL requires all copies to carry an appropriate copyright notice.

> (A) So with BSD license, I could study other source codes and apply it to my program, just ALWAYS acknowledge from where I got those source code, am I getting it right?

BSD is under the LGPL.   The changes to the source code don't have to be released.  Apple does not release the changes it has made to OSX from the Darwin (the version of FreeBSD that it is based on.)  

The GPL requires the source code to be released if the product is for sale.

> (C) Can I get some ideas from Open Source stuffs (but not the WHOLE source code), and apply it to my program and then sell it? Is it illegal? Or is the "Fair Use" applies? [http://en.wikipedia.org/wiki/Fair_use](http://en.wikipedia.org/wiki/Fair_use)

If it is under the GPL then you will be able to see the source code.  Yes, you can sell it, but you must release the source code too. 

> PLEASE FORGVE MY INQUISITIVENESS! 

We love inquisitive people here.  Keep asking away.

---

### Post by pmcastillo on 2006-12-26
Thanks guys! Rippey, azz, po0f, Sef!

Actually, I'm a programmer with a background of Visual Studio 6.0 and .NET, and some JAVA. I'm curious with all these Open Source Stuffs, and I am a believer of "Software Freedom". When I got a good grip with this Ubuntu, I'll try to help you guys...

I'll try more to read about these stuffs:
[http://en.wikipedia.org/wiki/GPL](http://en.wikipedia.org/wiki/GPL)
[http://en.wikipedia.org/wiki/BSD_license](http://en.wikipedia.org/wiki/BSD_license)

---

### Post by az on 2006-12-26
> **po0f said:**
> Sorry to be nit-picky, but [SQLite does](http://www.sqlite.org/copyright.html).  From what I hear [more than a few](http://www.python.org/download/releases/2.5/highlights/) people like it.

Er, sorry.  I meant in relation to Linux and open source.  If you look at the different licences of all the packages in the ubuntu archive, very few are PD.  PD does not encourage software freedom.  It is free software, but someone can turn around and take that freedom away.

BSD obliges you to attribute where the program came from.  GPL does that too, and also obliges you to release the software under the same licence under which you got it.  That does a better job at protecting your freedom and that's why the GPL is the most popular free-libre open source licence.

Releasing your code as PD does not do as good a job at stimulating a community around your work as the GPL.  You mention SQLlite, hoe do you compare that to MYSQL or PostgreSQL?  The latter two are much bigger projects.


> **pmcastillo said:**
> I get some ideas from Open Source stuffs (but not the WHOLE source code), and apply it to my program and then sell it? Is it illegal? Or is the "Fair Use" applies? [http://en.wikipedia.org/wiki/Fair_use](http://en.wikipedia.org/wiki/Fair_use)

I think the GPL is better than a BSD licence because it defines software freedom and enforces it.  The Mac operating system is based on a free operating system, but they then made it proprietary - something you cannot do with GPLed software.

Fair use is a copyright term.  It detracts from the meaning of freedom.  It used to be that you have unrestricted use of any work.  Copyright basically means that you have the exclusive rights to your work, which in of itself is fine and fair.  "Fair use" is almost always just a small subset of the rights that you would otherwise be entitled to to engage with the work in question.  Don't use the term fair use - it is jibberish and meant to confuse the consumer.

Can you take just a small piece of the source code and use it?   Sure!  You can use the whole thing or just a part.  You must abide by the licence, though, and under a GPL licence, you would have to attibute the work to the original author as well as release the source;  additionally, your whole application would have to be GPL licenced.

If you don't want to licence your whole app under the GPL, the Lesser GPL (LGPL) allows for interfacing a free software application with non-free ones.  But that's a slightly different story...  You would have to obtain your software bits from a LGPLed licenced application to keep your application proprietary.

> **pmcastillo said:**
> 
**QUESTION NUMBER 2:**  What are "black boxes"? Are they "illegally acquired codes"?


No, it's a computer running software that you know almost nothing about.  Since I can't study the source code of a proprietary application, it may as well be messing with my data, logging my keystrokes or otherwise spying on me.  There is a big demand for electronic voting machines to be based on free-libre open source software for this reason.

As more and more of our lives involve using computers, there is a need for software freedom (as well as the use of free formats) to ensure a certain level of privacy.  You can't ensure that privacy unless you use free-libre ope source software.

> **pmcastillo said:**
> 
**QUESTION NUMBER 3:** So to acquire a GPL license, I'll just say, "Hey, I decided to be a GPL, so abide the rules :)"? Or do I need to go GNU's office to acquire a license?

You need to distribute your software along with the licence.  That's it.  You pick the licence because you are the author.  You need to abide by the licence, too, which means making it possible for a user to obtain the source code.

There is also nothing preventing you from releasing vesion 2.2 of your software under the GPL and then releasing version 2.3 under a different licence.  You will not be able to prevent anyone from using version 2.2's source for forking (since it and it's derivatives will always be free under the GPL) and you will piss off the community you have built around your project, but as the author of the software, you get to chose.

---

### Post by az on 2006-12-26
> **pmcastillo said:**
> Can I get some ideas from Open Source stuffs (but not the WHOLE source code), and apply it to my program and then sell it? Is it illegal? Or is the "Fair Use" applies? 

I just had another thought about this.  To elaborate on my angst against the words "fair use", let's talk about software patent, because that may be what you meant to ask about.

You certainly can "get ideas" from Open Source stuffs.  In this case, let's mean Open Source stuffs to mean "free-libre, open source software (FLOSS).

FLOSS is not property.  Proprietary software is property.

Property, in the legal sense, has three kinds of laws to protect it, when talking about software.  Copyright, Trademark and Patent.

Copyright is your right to say "I wrote this, and this is what I want done with it..."

Trademark is something that is meant to protect the consumer by ensuring they are getting what they think they are getting when they buy a product of a certain name.

Patents are not something you can apply to sofware, but many countries don't realize this.  A patent is a mechanism which encourages a person to make public an invention that s/he would not otherwise make public, because they have a lot to lose by making their invention public.

If you had to invest a lot of time and effort to find a great way to do something, people will steal your ideas and you will have lost all that time and effort - so patents are there to protect you so that **you put in the time and effort to come up with great new ideas.**

The original intent of patents was to encourage people to go and invent new stuff.

In the software world, new ideas come so fast and are so small that you cannot innovate without building on past ideas.  It is a basic tennet in programming to reuse code, right?  Do not re-invent the wheel.

To patent software is not a good idea.  The only effect that patents can have on software is to stifle innovation.  The algorithyms that make up source code are not extraordinary feats of talent that require years of hard work to make, but small, incremental, logical progressions.  To say "I thought of this idea, I own the patent on it and you can't use my idea" is pretty much equivalent to someone patenting a book about "a man and a woman" and then preventing anyone else from writing that kind of book without paying a royalty -  it's that nonsensical.

Can you immagine a medical doctor not being allowed to research a particular disease because another doctor already took out a pentent on a cure for it?

So, sofware freedom takes a stance regarding software patents.  They are harmful to the software ecosystem and serve no one except the owner of the patent (who may not even be the author of the code!)

---

### Post by Engnome on 2006-12-26
You can also try the creative commons licenses. They are easy to select if you are unsure. Go to [http://creativecommons.org/license/](http://creativecommons.org/license/) and fill in the form, an appropiate license will be suggested.

---

### Post by az on 2006-12-26
> **Engnome said:**
> You can also try the creative commons licenses. They are easy to select if you are unsure. Go to [http://creativecommons.org/license/](http://creativecommons.org/license/) and fill in the form, an appropiate license will be suggested.

CC licences are not recommended for software.  Since compiled code is a lot differnent than a published story (you don't get to see the source code of the binary application, but the published story is only "source code") CC licences are not ideal...

CC licences also do not define freedom.  They let the individual authors do that.  That often leads to overy-restrictive licencing of works.  For example, the non-commercial clause is vague at best.

Imagine if the GPL had originaly had a non-commercial clause.  There would be no Apache or any other web servers using GPLed software.  No ISP would be able to use the software to run their web hosts or DNS servers because they make money.

So, If I wanted to use a CC-licenced non-commercial work to inspire a presentation I would give about a particular topic, I would not be able to use that content if I was paid to give the talk?

Anyway, the equivalent of the GPL in CC licences is the Attribution - Share Alike.


[http://wiki.creativecommons.org/FAQ](http://wiki.creativecommons.org/FAQ)

Can I use a Creative Commons license for software?

Creative Commons licenses are not intended to apply to software. They should not be used for software. We strongly encourage you to use one of the very good software licenses available today. The licenses made available by the Free Software Foundation or listed at the Open Source Initiative should be considered by you if you are licensing software or software documentation. Unlike our licenses -- which do not make mention of source or object code -- these existing licenses were designed specifically for use with software.

Creative Commons has &#8220;wrapped&#8221; some free software/open source licenses with its Commons Deed and metadata if you wish to use these licenses and still take advantage of the Creative Commons human-readable code and Creative Commons customized search engine technology. You can find more details here.

---

### Post by pmcastillo on 2006-12-29
One thing confuses me... This is how I analyse GPL:

> The GPL is the classic free-libre open source licence. It protects your four freedoms and obliges the recipient of the code to redistribute the changes under the same licence - that way, the software is always free.

The license that the licensor have, should be the license of the licensee will be... 

Therefore...

If the licensor gave it for free, I should give it also for free...
If the licensor gave the source codes, so I should give also the source code...

Therefore...

If get ideas (or source codes) freely from it, I can't make a program proprietary...
If I got their source codes openly from it, I can't make program closed-source...

It conflicts with this:

> Can you take just a small piece of the source code and use it? Sure! You can use the whole thing or just a part.

What's the meaning of "use" here? I can use it to make a proprietary software? Or I can only use it for another open-source software?

BTW, I saw something on the Internet like this: [http://www.theregister.co.uk/2001/06/02/ballmer_linux_is_a_cancer/](http://www.theregister.co.uk/2001/06/02/ballmer_linux_is_a_cancer/)
The content there is much like I'm asking asking right now. And wow! there's a real war about there between the open-source and the closed-source. :-|

---

### Post by az on 2006-12-29
> **pmcastillo said:**
> 
If get ideas (or source codes) freely from it, I can't make a program proprietary...
If I got their source codes openly from it, I can't make program closed-source...


You are correct.  I was refering to *ideas* from that portion of source code, in response to your question: "Can I get some ideas from Open Source stuffs (but not the WHOLE source code)"

I did not make my sentence very carefully...  No, you cannot reuse GPLed code without distributing it under the GPL as well.   Can you take the same idea, re-create it and then make it proprietary code?  Yes you can.  The GPL covers the code you write, not the idea behind it.  The GPL version three will even take proactive measures against software patents.

---

### Post by pmcastillo on 2006-12-29
Phew! Finally, all things are cleared up to me... :-D 

Can I get **ideas** from open-source then sell it? YES
Can I get **codes** from open-source then sell it? NO

GPL **license** things, not **patent** things...

Thanks man!

---

### Post by az on 2006-12-29
> **pmcastillo said:**
> 
Can I get **ideas** from open-source then sell it? YES

Sell, yes.  But most importantly, you can use them for any purpose.  It's not prohibited to sell GPLed software.  This is often done in conjunction with selling support.  You cannot distribute it without distributing the source code.  So you can't sell it without also making the source available.

> **pmcastillo said:**
> 
Can I get **codes** from open-source then sell it? NO


To be clear, you cannot re-use GPLed code and distribute it under any other licence than the GPL.  Whether you sell it or not is irrelevant - it's the fact that it's being redistributed that's important.


So, to rephrase your statement:

Can I get **ideas** from GPL-licenced code and then use it for another project? YES
Can I get **codes** from GPL-licenced code and then use it for another project? NO, not unless you distribute that project under the GPL as well.  And attribute the prior work to the original author.

---

### Post by Tomosaur on 2006-12-29
> **pmcastillo said:**
> 
1.) I made the program, then someone came at get my program, and RENAMED the name of my program, and redistribute it saying that its HIS work. Do I have any protection from these?


This would a _copyright_ issue. If they steal your code and rename it, then that is against the law in most places. The same would apply for any work, be it a book, or a painting or whatever.

> 
2.) What are these licenses (like the GPL)? What's the difference between giving the program with the source code, and saying, "Hey! I got a program for all of you guys, you change, edit, or do whatever you want", and the difference between having a license?

The GPL allows people to modify the code and release a program which uses it. They cannot, however - claim it is your version. They are also bound legally to release whatever program they make under the GPL - meaning they cannot place a restrictive license on your code. There is a certain element of trust involved. The GPL does not mean you have to release your program for free. What it means is that the CODE must be available to those who use your program. The artwork and documentation/support can all be under different licenses if you feel they require more protection.

> 3.) What do I need to do to obtain a license? (like GPL)
Nothing - just put the GPL text at the top of each of your source code files, and one in the installer program, if applicable. The GPL also requires you to place a copyright notice into your code.

I think a standalone GPL text file is also required.

---

