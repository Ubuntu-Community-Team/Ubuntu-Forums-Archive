---
title: "[SOLVED] Firefox Download error 228 - Cannot install del.icio.us Extension"
date: 2007-12-11
forum: General Help
---

### Post by NickGray on 2007-12-11
I am using Ubuntu 7.10 and Firefox 2.0.0.11.
I am trying to install [the del.icio.us extension for Firefox]("https://addons.mozilla.org/en-US/firefox/addon/1532"), but I keep getting an error.

Firefox reports: ```
Firefox could not install the file at https://addons.mozilla.org/en-US/firefox/downloads/file/15592/del.icio.us_buttons-1.2.1-fx.xpi 
because: Download error -228
```

I researched **Download error 228**, and it suggested that I download the XPI file directly. Can anyone try this out - can you download this file and save it to your desktop?  [https://addons.mozilla.org/en-US/firefox/downloads/file/15592/del.icio.us_buttons-1.2.1-fx.xpi](https://addons.mozilla.org/en-US/firefox/downloads/file/15592/del.icio.us_buttons-1.2.1-fx.xpi)

I can't. My FIrefox hangs on "Starting..." and if I type that into the URL field, it says "Waiting for addons.mozilla.org..."

Any advice?

---

### Post by NickGray on 2007-12-13
Perhaps it was my DNS that was timing out on the https: link...
**Confirmed Fix** - Download the file directly from the Mozilla FTP site  ([LINK HERE]("http://ftp.mozilla.org/pub/mozilla.org/addons/1532/del.icio.us_buttons-1.2.1-fx.xpi")).

---

