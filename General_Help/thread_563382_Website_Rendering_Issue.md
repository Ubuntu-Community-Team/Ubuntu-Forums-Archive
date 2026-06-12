---
title: "Website Rendering Issue"
date: 2007-09-29
forum: General Help
---

### Post by Dylnuge on 2007-09-29
Hello,

I notice that websites in Firefox under Linux have a small annoyance when rendering the pulldown menus, like those on [www.adobe.com](www.adobe.com). I am not exactly sure how to describe it, but it is like the menus are at the bottom layer, and graphics, flash videos, and more obstruct them.

I do not have this problem in Firefox for Windows. Any ideas on what may cause the problem?

---

### Post by defrex on 2007-09-29
Flash always takes the top layer by force. This was the case in windows last time I checked (admittedly probably a year or so ago). I guess it doesn't happen anymore if adobe.com (the owner of flash) has the problem. I would blame the flash plugin myself, but either way I doubt there's an easy solution.

---

### Post by michaelzap on 2007-09-30
Actually, this is a problem specific to the Linux versions of Firefox and Flash. It's been possible to overlay drop-down menus and other elements over Flash for a while in Windows. But it still doesn't work in Linux.

---

### Post by acron1 on 2007-09-30
I have the same problem with Firefox. If this problem is solved in Windows why not in Linux?

---

### Post by Jonne on 2007-09-30
It's certainly possible to do it so it looks ok in Firefox on Linux too. We have made another website that uses flash and a div overlay where the div would stay on top (on Windows, Linux and OS X). I guess Adobe isn't aware of how to get around the limitations of their own flash player or something.

---

### Post by Dylnuge on 2007-09-30
Funny that I noticed it on the Adobe website and it turns out to be an Adobe problem. Interestingly enough, I never noticed this problem in the old Macromedia website. (I thought it was an adblock problem, but I disabled adblock with no avail).

Flash is the only technology I still use VMWare for. Well, that and a few other things, but mainly Flash. Hope Adobe comes to their senses and releases all of their technology for Linux, but they could start by fixing a flash problem.

---

### Post by michaelzap on 2007-09-30
> **Jonne said:**
> It's certainly possible to do it so it looks ok in Firefox on Linux too.

How? I haven't put much effort into figuring it our because I assumed that it's a limitation of my Flash plug-in (and thus not really a web design problem). I can make Flash stay underneath other elements easily in Windows or OSX, but it doesn't behave the same way in my Ubuntu environment.

---

### Post by Jonne on 2007-09-30
setting
<param name="wmode" value="transparent" />
should be enough. (and maybe making sure the z-index of the div is higher than your object tag).

I haven't had much problems with Linux in this regard, Firefox on Mac OS X is worse (but it works there too, unless you use css opacity).

anyway, I hate Flash regardless, and i avoid using it when i can.

---

### Post by michaelzap on 2007-09-30
> **Jonne said:**
> setting
<param name="wmode" value="transparent" />
should be enough. (and maybe making sure the z-index of the div is higher than your object tag).

Works on my Windows machines (virtual and real), but not in Ubuntu. I suspect my Flash plugin. Maybe I should go look for an updated version...

> **Jonne said:**
> anyway, I hate Flash regardless, and i avoid using it when i can.
Amen to that. But some clients insist on whiz-bang hoop-de-doo, and it is one of the two best ways to embed video (the other being QuickTime, imo). Lately we've been using SIFR so we can make the title text in sites any crazy font we like, and since those are usually right below the drop-down menus...

---

### Post by michaelzap on 2007-09-30
> **michaelzap said:**
> Works on my Windows machines (virtual and real), but not in Ubuntu. I suspect my Flash plugin. Maybe I should go look for an updated version...

Updated to the latest version - no change.

---

