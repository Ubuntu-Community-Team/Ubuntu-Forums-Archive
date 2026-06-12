---
title: "Using wget to get IPTV playlist"
date: 2022-11-18
forum: General Help
---

### Post by ptmuldoon on 2022-11-18
I am trying to download my IPTV provider playlist (to use with TvHeadend) and having some issues with wget.

If I type the below in a browser, I will be prompted to save a file.

[https://MYIPTVPROVIDER.com/get.php?username=USER&password=PASS&type=m3u_plus&output=ts](https://MYIPTVPROVIDER.com/get.php?username=USER&password=PASS&type=m3u_plus&output=ts)

But when I try something like the below with wget I get a 404 error

wget -O epg.xml [https://MYIPTVPROVIDER.com/get.php?username=USER&password=PASS&type=m3u_plus&output=ts](https://MYIPTVPROVIDER.com/get.php?username=USER&password=PASS&type=m3u_plus&output=ts)

Is there something else I'm missing and doing incorrectly?

Thank you
PT

EDIT.   I got it figured out and need to imitate a browser like such:

wget -O epg.xml --user-agent=Mozilla --content-disposition -x --load-cookies cookies.txt "http://URLADDRESS"

---

### Post by TheFu on 2022-11-18
**Put the URL inside ''.**  99% certain that will fix it.

The '&' character is likely the issue, but there are other problem characters in URLs.

I pull the PlutoTV list every 4 hrs (they only provide schedule data 6 hrs at a time).

If this fixes the issue, please take the time to 
a) explain the solution
b) mark the thread as 'SOLVED" using the "thread tools" links near the top, to help others more easily find the solution. This toggles a flag in the DB, so searched for "SOLVED" threads is fast.

---

