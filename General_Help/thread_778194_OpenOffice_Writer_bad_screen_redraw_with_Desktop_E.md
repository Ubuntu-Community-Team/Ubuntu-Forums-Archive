---
title: "OpenOffice Writer bad screen redraw with Desktop Effects"
date: 2008-05-01
forum: General Help
---

### Post by parsim on 2008-05-01
If I turn on Desktop Effects ("Normal"), then scroll a document in OpenOffice Writer, it often becomes messed up (see attachment).

This only happens when I scroll with the keyboard (PageUp, cursor keys, typing in new text), not the mouse. All other apps seem to work fine.

Any tips?

Using restricted NVIDIA driver on AMD64, Ubuntu 8.04.

---

### Post by glacialfury on 2009-02-10
This occurs to me as well.  I have Compiz/Beryl running, using proprietary NVIDIA drivers.  I can't say if it's just keyboard, haven't paid that much attention to it, but it certainly happens simply while typing long documents - especially seems to happen when the typing goes from one page to the next, and Writer scrolls down for you.

Scrolling up or down will force it to redraw, but it won't redraw unless you do something like that to make it.

---

### Post by aldeby on 2009-04-18
I've experienced this issue too.
Here I explained the workaround: [http://aldeby.org/blog/index.php/fix-for-openoffice-writer-bad-screen-redraw-refresh.html]("http://aldeby.org/blog/index.php/fix-for-openoffice-writer-bad-screen-redraw-refresh.html")

---

### Post by dtoronto on 2009-04-18
I had similar issues with Intrepid Ibex and Open Office.  Fixed them with an upgrade to Open Office 3.

---

### Post by giovannilenzi on 2009-05-19
I've experienced this issue too on Ubuntu 8.04 and 9.10 using OpenOffice and Wine.
I solved it following your instructions, I mean:

> System -> Preferences -> CompizConfig Settings Manager navigate to Utility section and click on Workarounds plugin. Inside enable (tick) &#8220;force synchronization between X and GLX&#8221;.

But this was not sufficient, I had to change some values in the Appearance Preferences and in the Font rendering, see the attachments.
The changes are applied immediately.

---

### Post by Dan_Dranath999 on 2009-06-02
I'll try that when i get home...

---

### Post by Dan_Dranath999 on 2009-06-18
the option "force syncronization between X and GLX" is not present??? (i'm using Hardy -Maybe it's because it's in spanish, but i don't see anything similar to that option-)

---

### Post by jolindbe on 2009-07-02
> **Dan_Dranath999 said:**
> the option "force syncronization between X and GLX" is not present??? (i'm using Hardy -Maybe it's because it's in spanish, but i don't see anything similar to that option-)

The same for me! I'm on Inrtrepid, though in Swedish, but no "force synchronization between X and GLX"-option. How do I get this?

---

### Post by meatlover on 2009-07-08
I have a nvidia 9300S M with driver 185.18.14.  I'm also running Compiz.  I checked the "Force Synchronization...." option.  This didn't fix the problem for me in general.  However, it does allow me to view .odt documents without error.  I noticed one thing:  If you scroll the document by dragging the scroll bar, the lines aren't as dramatic.  I get the worst redraw when I use the scroll pad on my laptop.

---

