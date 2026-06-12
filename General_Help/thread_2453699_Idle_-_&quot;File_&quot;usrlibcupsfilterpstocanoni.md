---
title: "Idle - &quot;File &quot;/usr/lib/cups/filter/pstocanonij&quot; not available: No such file or direct"
date: 2020-11-15
forum: General Help
---

### Post by ardouronerous on 2020-11-15
I'm running Xubuntu 20.04.

I'm trying to get my Canon PIXMA iP2700 printer to work off a custom PPD file. I've placed the PPD file in **[FONT=courier new]/home/~/.local/share/ppd/canonip2700.ppd[/FONT]**.

I went to [http://localhost:631/](http://localhost:631/) and directed my printer to the PPD file. However, I get this message:

   [TABLE="class: list"]
[TR]
[TH]Queue Name
[/TH]
[TH]Description[/TH]
[TH]Location[/TH]
[TH]Make and Model[/TH]
[TH]Status[/TH]
[/TR]
[TR]
[TD]Canon-iP2700-series
[/TD]
[TD]Canon iP2700 series[/TD]
[TD]~
[/TD]
[TD]Canon iP2700 series Ver.3.90
[/TD]
[TD]Idle - "File "/usr/lib/cups/filter/pstocanonij" not available: No such file or directory"
[/TD]
[/TR]
[/TABLE]

Now, there is a driver available in CUPS for my printer, however, the print quality available is "Standard," which is a waste of ink though. The PPD file I provided has "Draft" quality included, which is why I want to use it for my printer.

How can I fix this, thanks.

---

### Post by ardouronerous on 2020-11-15
If it could help, here's the contents of **[FONT=courier new]canonip2700.ppd[/FONT]**: [https://paste.ubuntu.com/p/ptQKdtTYt9/](https://paste.ubuntu.com/p/ptQKdtTYt9/)

---

### Post by ActionParsnip on 2020-11-15
Seems you need the cnijfilter-common package

Source 
[https://groups.google.com/g/alt.os.linux.mandriva/c/S-ws__QL5NU?pli=1](https://groups.google.com/g/alt.os.linux.mandriva/c/S-ws__QL5NU?pli=1)

Grab a deb of that or search software centre etc

---

### Post by ardouronerous on 2020-11-15
> **ActionParsnip said:**
> Seems you need the cnijfilter-common package  Source  [https://groups.google.com/g/alt.os.linux.mandriva/c/S-ws__QL5NU?pli=1](https://groups.google.com/g/alt.os.linux.mandriva/c/S-ws__QL5NU?pli=1)  Grab a deb of that or search software centre etc  The only cnijfilter-common package I could find for my printer is 32-bit though: [https://www.canon.com.au/printers/pixma-ip2700/support](https://www.canon.com.au/printers/pixma-ip2700/support)  How do I install this?

---

