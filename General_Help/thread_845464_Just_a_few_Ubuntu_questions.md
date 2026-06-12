---
title: "Just a few Ubuntu questions"
date: 2008-06-30
forum: General Help
---

### Post by BiggieD on 2008-06-30
Hi. I'm wanting to switch from Vista and noticed Ubuntu. I am a not really that clear on what I can do with Ubuntu though.
I was wanting to know, can I run everything that I can run on Windows? Also, what about software such as Logic on Apple? Would I be able to run this software?

Also, I am installing this to a Aspire 5100 laptop. Will the Ubuntu OS be able to run my in-built wireless reciver and built-in webcam?

My last question is, will I be able to run Ubuntu along-side Vista for a while? Just to try out the OS before I get rid of Vista?

Many thanks (sorry if these questions are already answered. I couldn't find anything which answers my questions specifically)

---

### Post by russlar on 2008-06-30
> **BiggieD said:**
> Hi. I'm wanting to switch from Vista and noticed Ubuntu. I am a not really that clear on what I can do with Ubuntu though.
I was wanting to know, can I run everything that I can run on Windows? Also, what about software such as Logic on Apple? Would I be able to run this software?

Also, I am installing this to a Aspire 5100 laptop. Will the Ubuntu OS be able to run my in-built wireless reciver and built-in webcam?

My last question is, will I be able to run Ubuntu along-side Vista for a while? Just to try out the OS before I get rid of Vista?

Many thanks (sorry if these questions are already answered. I couldn't find anything which answers my questions specifically)

Sure! Ubuntu 8.04 includes wubi, which installs ubuntu inside your windows partition. This doesn't change anything inside of windows, except giving you the option to boot to ubuntu or windows.

---

### Post by Gunman1982 on 2008-06-30
> **BiggieD said:**
> Hi. I'm wanting to switch from Vista and noticed Ubuntu. I am a not really that clear on what I can do with Ubuntu though.
I was wanting to know, can I run everything that I can run on Windows? Also, what about software such as Logic on Apple? Would I be able to run this software?

Run every program from windows on Ubuntu? No
Run similar programs which are developed for linux with similar functionality? Yes most of the time. Depends on the stuff you want to do though.
Run a specific program for windows which is not available for linux (ubuntu)? Maybe, you can try through using the wine program. It tries to execute windows programs on linux.

> **BiggieD said:**
> Also, I am installing this to a Aspire 5100 laptop. Will the Ubuntu OS be able to run my in-built wireless reciver and built-in webcam?

Don't know because I don't know which hardware is built into your Aspire 5100 and I'm to lazy to look. You can try out ubuntu by running the live cd without changing anything on your system/windows installation.

> **BiggieD said:**
> My last question is, will I be able to run Ubuntu along-side Vista for a while? Just to try out the OS before I get rid of Vista?

Yes you can either install wubi which creates a file on your harddisk where linux (ubuntu) works in so you don't even need to repartition anything. Or you shrink your windows partition and install ubuntu on the free diskspace. 

> **BiggieD said:**
> Many thanks (sorry if these questions are already answered. I couldn't find anything which answers my questions specifically)

Maybe you didn't look in the right place? ;) At least the last question should be answered on the faq site of ubuntu.com.

---

### Post by Taxman415a on 2008-06-30
Ubuntu has software that can do basically everything that Windows can do, but you can't always just run the Software you would buy and install for Windows unless you run Windows in an emulator on Ubuntu (which you can do).

I don't know what Logic is, maybe someone else does or you can point to a link or something. Based on a quick google search for your laptop and linux I only found old posts. This is generally a good sign indicating that most issues have been fixed since then. You may need to use ndiswrapper to install drivers for your wireless card, but that does work once you read up on how to do it. 

Your best bet is to download the livecd and boot from that and see how it runs on your hardware. Then you can look for solutions for anything that doesn't work right out of the box. And yes, you can definitely run Ubuntu alongside Windows, it's called dual booting. The Ubuntu installer can set that up for you very easily.

Other tip is now that we've given you some pointers, try googling for more.

---

### Post by Greyed on 2008-06-30
> **BiggieD said:**
> Hi. I'm wanting to switch from Vista and noticed Ubuntu. I am a not really that clear on what I can do with Ubuntu though.

Well, what do you do with Windows now?  

I must preface the following answers with this disclaimer.  I'm gonna be honest and blunt.  But read on to the end.

> I was wanting to know, can I run everything that I can run on Windows?

No.

> Also, what about software such as Logic on Apple? Would I be able to run this software?

Probably not so call it a no.

> Also, I am installing this to a Aspire 5100 laptop. Will the Ubuntu OS be able to run my in-built wireless reciver and built-in webcam?

Maybe but that depends on the driver support.  Hardware manufacturers are notorious for slapping together something for Windows, maybe Mac if you're lucky and calling it a day.  The rest of the time it's many hours of trial-and-error by third party developers to make drivers that work; and often once done work better than the originals.

The best answer for any hardware compatibility is to do a Google search of the exact model and tack on "linux", "ubuntu" or "debian" on the end.  For example "Aspire 5100 linux" = [http://www.google.com/search?q=aspire+5100+linux](http://www.google.com/search?q=aspire+5100+linux)

> My last question is, will I be able to run Ubuntu along-side Vista for a while? Just to try out the OS before I get rid of Vista?

Yes.  Even better the Ubuntu CD is a live-CD which means you can try it out without installing a thing on your hard drive.  Something that is whole-heartedly recommended.

Now, with the nitty gritty out of the way let me back up a bit.  You have a statement and a question which are something at odds with one another.  You say you don't know what you can do with Ubuntu but then ask if it will run Windows apps.

Remember I asked "What do you do with Windows?"

Here's a short answer for some tasks.  The bolded programs also have Windows versions.

Email?

Evolution or **Thunderbird**

Web?  

**Firefox** or **Opera**

Office applciations?

**OpenOffice.org**

Graphic editing?

**The GIMP** and/or **Inkscape**

Something else?  Try it under WINE which provides a Windows compatibility layer.  Some Windows programs run fine, others do not.  Which is why the answer to your first question of whether Ubuntu can run *all* Windows software.

Basically with a few exceptions (gaming being a large one) **what** you do on Windows you can do on Ubuntu, only **how** you do it might differ.  As you can see from the list above, depending on what you want to do you can even give them a whirl on Windows natively.

---

