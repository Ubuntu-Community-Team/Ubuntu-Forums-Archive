---
title: "Firefox strange rendering on some pages"
date: 2008-07-07
forum: General Help
---

### Post by pencilcheck on 2008-07-07
It start happening after ff3 I think.

See attachments for screenshots.

How to reproduce:
1. Open FF3
2. go to website like: [http://blogs.adobe.com/penguin.swf/2007/01/flash_player_9_for_linux_x86.html](http://blogs.adobe.com/penguin.swf/2007/01/flash_player_9_for_linux_x86.html)

or

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

3. try to scroll the page and you will see.

---

### Post by blackhatbrigade on 2008-07-07
Maybe a plugin issue?  Although I didn't see anything on those pages that used a plugin.  I have ff3 and I didn't have any problems viewing those pages.

---

### Post by sports fan Matt on 2008-07-07
It scrolled well on my system as well.  Sorry I cant be of more help.

---

### Post by cpetercarter on 2008-07-07
Well, both pages scroll fine in ff3 on my computer, so I guess that the problem arises from specific hardware/plugins on your computer.

From the screenshots, you seem to have a large number of apps and windows open on your computer. It might help in pinning down the problem if you tried to view the pages with nothing except Firefox open. Also, try disabling all your Firefox extensions/plugins and then re-enablng them one at a time to see if any ofthem are the problem.

---

### Post by nikgare on 2008-07-07
It looks like it could either be a graphic driver problem, or a problem with firefox - which version of firefox are you using, and which graphic card and driver are you using?

---

### Post by AnonCat on 2008-07-07
I suspect a graphics driver problem.  I had similar issues when I tried to get a TNT2 graphics card working in Ubuntu.

---

### Post by pencilcheck on 2008-07-07
I had NVIDIA 8400M GS.
Well, that is only in the screenshots actually it happens even if I have only one firefox tab opened without any other apps filling the screen.

For the plugins and extensions suspicion, I would try to open in safe mode and see if things are fixed.

---

### Post by pencilcheck on 2008-07-07
It still happens after I open firefox in safe mode. So it's not the plugins issue.
And I also found out that it happens in Epiphany Browser too! Same symptom with fragments of the web content brushed horizontally throughout the page when scrolling the page.

---

### Post by nikgare on 2008-07-10
Which driver are you using for your graphic card?
Maybe you need to use a newer one or a slightly older one to get the best performance?

---

### Post by pencilcheck on 2008-07-10
I'm using 173.14.09
I'm not sure if downgrading to a older driver would help.
If you can explain more?

---

### Post by nikgare on 2008-07-11
> **pencilcheck said:**
> I'm using 173.14.09
I'm not sure if downgrading to a older driver would help.
If you can explain more?
I'm not sure that it would help either, but it sure can't make things worse ;-)
Maybe you card works better with a different version?

Have you tried removing firefox, rmoving .mozilla/firefox directory and reinstall firefox?

Looking at the tabs in the screen grabs you posted it seems to be going wrong on flash sites -is this right?

---

### Post by pencilcheck on 2008-07-17
not necessarily flash sites.

---

### Post by nikgare on 2008-07-19
If you create a new user and try firefox out there does the problem still appear?

---

### Post by pencilcheck on 2008-07-24
I haven't tried it yet. but in arch it's working fine. and it uses the same nvidia driver. I wonder what causes it?

---

