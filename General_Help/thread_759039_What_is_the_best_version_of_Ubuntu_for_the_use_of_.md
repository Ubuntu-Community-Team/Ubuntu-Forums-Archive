---
title: "What is the best version of Ubuntu for the use of Digital Signage?"
date: 2008-04-18
forum: General Help
---

### Post by Bdanger on 2008-04-18
I'm wondering what version/build of Ubuntu is the best for the use of digital signage.  

Here is what I am looking for:
-The version that has the most community support out there
-Can smoothly run media applications without using too much processing power

Basically I'm trying to pair up a stable Ubuntu linux desktop running media with cheap hardware (maybe a MINI-ITX embedded motherboard) and an LCD to run Digital signage.  I want to be able to access it via an internet connection and modify any settings.  But I think the first step is matching the right software with the right hardware.  Any comments would be appreciated!

---

### Post by ibuclaw on 2008-04-18
All Ubuntu systems run on the same kernel. (As of Hardy that now is the 2.6.24-16)

All support for hardware is with using this kernel plus a few external modules.

So to answer your question, all versions are good at it.

Proof of concept.
[http://noticebox.net/home](http://noticebox.net/home)
Ubuntu with Digital Signage running straight off. (I think you have to pay for it though)

I can't find anything about digital signage in the repositories, but you can have a good look round at sourceforge to see if there are anything that you can get started with the hardware you have.
[http://sourceforge.net/search/?type_of_search=soft&type_of_search=soft&words=digital+signage](http://sourceforge.net/search/?type_of_search=soft&type_of_search=soft&words=digital+signage)

Regards
Iain

---

### Post by HermanAB on 2008-04-18
It sounds like Linux Mint is what you want.

---

### Post by LeoSolaris on 2008-04-18
All of the versions have the same support, either by buying support that you can call on demand, or by asking us here on the forum and waiting for an answer for free.

As for what you're attempting, It should run just fine for that, desktop or server. Desktop would probably be easier to set up if you do not know how to use the terminal. (Command line)

If it is slides of images your after, you can do that with Openoffice.org's Presentation, just set it to full screen and keep the mouse and keyboard unplugged when you want it to run for customers (to keep them from disrupting the display!)

That would be the needlessly heavy way to do it, but effective and the simplest to set up if you're not technically inclined.
Leo

I would bet that NoticeBox would be the most effective solution, but it does look like it will cost a bit.

---

### Post by Bdanger on 2008-04-18
> **HermanAB said:**
> It sounds like Linux Mint is what you want.

What are the advantages of Linux Mint over regular Ubuntu?  What does it mean that it has "integrated media codecs?"

From what I can see on the website it seems as though it is just a more user-friendly distro of Ubuntu.

> **LeoSolaris said:**
> ...If it is slides of images your after, you can do that with Openoffice.org's Presentation, just set it to full screen and keep the mouse and keyboard unplugged when you want it to run for customers (to keep them from disrupting the display!)

That would be the needlessly heavy way to do it, but effective and the simplest to set up if you're not technically inclined.
Leo

I would bet that NoticeBox would be the most effective solution, but it does look like it will cost a bit.

I've heard of NoticeBox but I think I have the capabilities to do something better on my own.  I'm not looking for slides of images, I plan to have a media player loop a set of media files that are in a certain folder.  I'd like to have support for .wmv, .swf, DIVX, and maybe a few more.  From there I can ftp into the folder and update it whenever necessary.

...it seems like this thread is moving along.  Now it's on to the hardware forum to find a good hardware setup...:)

any more comments and suggestions are still welcome though!

---

### Post by srilyk on 2008-06-04
I'd probably use VLC for the media player, as it usually handles filetypes rather well.

---

