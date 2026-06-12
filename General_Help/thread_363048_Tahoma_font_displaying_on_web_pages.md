---
title: "Tahoma font displaying on web pages"
date: 2007-02-16
forum: General Help
---

### Post by myname on 2007-02-16
I installed the Tahoma font off the office CD, and installed the MS core fonts, however, web pages that are designed with the tahoma font look horrible.  

I work with a couple clients who insisted on the tahoma font for the default font for their website, however, when brought up in either Firefox or Konqueror, it looks horrible;

[www.litescapes.biz/index.php](www.litescapes.biz/index.php)

Any idea how to get the tahoma font to render?

--Kevin

---

### Post by llamakc on 2007-02-16
It looks poorly on your computer? It renders fine on mine. How about a screenshot?

---

### Post by myname on 2007-02-16
lets see if this works, my first time sending in a screenshot.  

Plz note, the fonts on this page should render clean, if you can view it from a windows box.

[ATTACH]25430[/ATTACH]

---

### Post by llamakc on 2007-02-16
I am confused as to the problem. Are your clients using Ubuntu to view the pages? Or is your web-server running Ubuntu? Or, is the problem that the page looks differently for you as the developer when comparing them on Windows and Ubuntu?

---

### Post by bmt on 2007-02-16
Have you tried inhibiting antialiasing below x pixels?  It's a system setting (not sure where in KDE), but it made a difference for me.

The link rendered fine for me (Dapper, Gnome, Opera).

---

### Post by myname on 2007-02-16
> **llamakc said:**
> I am confused as to the problem. Are your clients using Ubuntu to view the pages? Or is your web-server running Ubuntu? Or, is the problem that the page looks differently for you as the developer when comparing them on Windows and Ubuntu?

The server is a Windows 2000 server, running IIS.  The site looks fine when rendered in IE or Firefox on a windows browser, but when the site is loaded in Firefox and Konqueror in Kubuntu, the text does not look the same, even though I have the Tahoma font as well as the MS Core Fonts installed.

Any ideas?

--Kevin

---

### Post by llamakc on 2007-02-16
> **myname said:**
> The server is a Windows 2000 server, running IIS.  The site looks fine when rendered in IE or Firefox on a windows browser, but when the site is loaded in Firefox and Konqueror in Kubuntu, the text does not look the same, even though I have the Tahoma font as well as the MS Core Fonts installed.

Any ideas?

--Kevin

Are you expecting it to look precisely the same? Ubuntu doesn't use ClearType.

---

### Post by FluffyElmo on 2007-02-16
I'd investigate the anti-aliasing settings mentioned by bmt...it does look a little hard to read on my box but increasing the text size one or two notches in Firefox smooths things out.

---

