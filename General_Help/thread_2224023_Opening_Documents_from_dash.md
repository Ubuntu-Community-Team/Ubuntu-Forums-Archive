---
title: "Opening Documents from dash"
date: 2014-05-14
forum: General Help
---

### Post by avesummathat on 2014-05-14
Since upgrading to 14.04, clicking on a document in the dash opens a preview of the document, rather than the document itself. I then have to click "open" to open it.

I'm sure there's a setting somewhere to make this behave normally (open the document), but I can't find it in dconf-editor, nor ccsm...

---

### Post by avesummathat on 2014-05-14
Solved it!
[http://www.omgubuntu.co.uk/2013/06/the-new-click-behaviour-in-the-dash](http://www.omgubuntu.co.uk/2013/06/the-new-click-behaviour-in-the-dash) still applies for 14.04

Open dconf-editor > com > canonical > unity > uncheck "double-click-active"

---

