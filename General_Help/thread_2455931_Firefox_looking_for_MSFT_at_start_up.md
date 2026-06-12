---
title: "Firefox looking for MSFT at start up"
date: 2020-12-30
forum: General Help
---

### Post by Kenzo on 2020-12-30
Why does Firefox look for Microsoft MSFT server on port 443 at start up?

---

### Post by walts48 on 2020-12-31
> **Kenzo said:**
> Why does Firefox look for Microsoft MSFT server on port 443 at start up?

Ask Mozilla [https://support.mozilla.org/en-US/products/firefox](https://support.mozilla.org/en-US/products/firefox)

I have no idea what it looks for at start up other than my home page and probably Cloudflare since I have DoH enabled.

How did you determine this connection?

---

### Post by Kenzo on 2020-12-31
[QUOTE
How did you determine this connection?[/QUOTE]

I blocked all out traffic, started Firefox and check the logs.  Firefox wants to connect to Amazon servers at start up too but this is a known. Just wondering why wants to connect to MSFT. Seems a bit superfluous. FF won't start unless it connects to Microsoft MSFT server. Seems a bit odd to me.

---

### Post by Kenzo on 2021-01-01
I found the answer... DDG is the search engine I had setup in FF.  DDG page is on the MS server 20.43.111.112

---

### Post by walts48 on 2021-01-01
> **Kenzo said:**
> I found the answer... DDG is the search engine I had setup in FF.  DDG page is on the MS server 20.43.111.112

That's very interesting. Thanks for the update. :)

---

