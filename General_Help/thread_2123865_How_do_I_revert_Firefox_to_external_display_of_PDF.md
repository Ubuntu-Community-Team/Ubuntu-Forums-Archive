---
title: "How do I revert Firefox to external display of PDFs?"
date: 2013-03-09
forum: General Help
---

### Post by Colin@oxford on 2013-03-09
Recent auto-upgrade to FF 19.0 gives me PDFs displayed in a browser window rather than the previous behaviour of asking me whether I want to save it or view it.  I know some poeple want this but I prefer it as it was.  How do I set it back?  The solution on the FF help page says to choose Edit->Preferences and the "Applications" tab and set PDF to "Always ask".  Well it is!  And there is not a "preview in firefox" either.  Yes, I have rebooted the computer since the upgrade.  Any suggestions?

---

### Post by mike555 on 2013-03-09
deleted

---

### Post by Impavidus on 2013-03-09
Go to about:config (type it in the address bar), click away the warning and search for pdfjs.disabled. Right click on it and toggle to set it to true. Maybe that helps.

---

### Post by claracc on 2013-03-09
Firefox 19.0.2 shows more options:

You can try: see in document viewer (default)
or use other

---

### Post by Colin@oxford on 2013-03-09
> **Impavidus said:**
> Go to about:config (type it in the address bar), click away the warning and search for pdfjs.disabled. Right click on it and toggle to set it to true. Maybe that helps.

That did it. Thanks!!

---

