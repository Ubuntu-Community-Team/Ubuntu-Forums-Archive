---
title: "OpenOffice.org Line Spacing Difference"
date: 2008-01-12
forum: General Help
---

### Post by phildaman46 on 2008-01-12
I have some documents that I made in Windows XP.  When I open them in Ubuntu, the line spacing is different.  How do I fix this problem so it looks the same as in XP?

---

### Post by steeleyuk on 2008-01-12
Two questions.

What program did you use to create them originally?
What format did you save them in?

---

### Post by phildaman46 on 2008-01-12
I used OpenOffice.org to make the documents and they are saved as OpenDocument (ODT).

---

### Post by steeleyuk on 2008-01-12
In that case I'd have thought everything would be the same. Check the line spacing in Format > Paragraph > Indents and spacing tab.

Also check the font you used in Windows. By default Ubuntu does not have the same fonts that Windows does however you can install them by grabbing [msttcorefonts]("apt://msttcorefonts") from the repo.

---

### Post by phildaman46 on 2008-01-12
Msttcorefonts is already installed. For some reason if I copy and paste a document to a new one, the line spacing is the same as in Windows Xp.  I don't get why it does this.  I don't want to have to do that with all my documents to fix the line spacing annoyance.

---

### Post by phildaman46 on 2008-01-16
Does anyone else have this problem with line spacing in OpenOffice.org?

---

### Post by amak79 on 2008-04-29
phildaman46,

Did you end up solving this as I have exactly the same issue that you described. I'm also using the Liberation font which is a free font available on Linux and Windows and still the line spacing different. Comparing the printed documents side by side shows that line spacing is smaller on Linux, even though the line settings are the same.

---

### Post by phildaman46 on 2008-05-17
I never found a solution to this problem, sorry. It seems nobody else has the same or similar problem.

---

### Post by amak79 on 2008-05-17
> **phildaman46 said:**
> I never found a solution to this problem, sorry. It seems nobody else has the same or similar problem.

Thank you for the reply. If I do find a solution I'll let you know.

---

### Post by phildaman46 on 2008-05-17
Sorry for the late reply. I haven't checked this thread in awhile.

---

### Post by SteveHoffmanUK on 2008-05-20
I have had the line spacing problem pretty consistently when I opened .odt files in Ubuntu Open Office that had been created in OO Windows. Even though OO Ubuntu said that the spacing was single, it was greater than the single spacing in the OO Windows version. For example, the very same document that took 16 pages in OO Windows took 20 in Ubuntu.

The solution that worked for me was to go into the Windows/Fonts folder, copy all the TTF (true type fonts) fonts, then paste them into Ubuntu. I **think** it's usr/share/fonts/TTF, but I may be wrong. Once I did that, the line spacing in OO Ubuntu looked the same as in OO Windows. Why this worked I have no idea. 

I've recently switched to PCLinuxOS, and I didn't have this problem with that particular distro. Slightly off-topic, I've just today run into a similar problem in OO between Windows XP and Vista :shock: What fun.

---

