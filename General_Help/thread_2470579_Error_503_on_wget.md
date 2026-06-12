---
title: "Error 503 on wget"
date: 2022-01-04
forum: General Help
---

### Post by snadegg on 2022-01-04
Wget worked for ~3 weeks, but now when trying to wget from certain websites I get an error 503. I haven't downloaded more than 5 files in one day from the sites in question.

I've tried using --no-proxy and setting user-agent to no avail.

I've also tried using cURL but it only downloads the HTML code of the download page, even using the -L tag.

If anyone can help me get either command working I would very much appreciate it!

---

### Post by Impavidus on 2022-01-05
503 (Service Unavailable) is a server error. It's unrelated to any action of yours, like sending too many requests, which would give error code 429. That is, assuming that the maintainer of the server set it up to provide the appropriate status codes. It looks like there's nothing you can do about it.

---

### Post by slooksterpsv on 2022-01-07
Impavidus is correct. You can try wget on a site like.... ubuntu.com and it should just download the home page - that way you can validate that your network connection is fine. But yes, impavidus is right, 503 is Service Unavailable - meaning the server is down or isn't responding to requests.

---

