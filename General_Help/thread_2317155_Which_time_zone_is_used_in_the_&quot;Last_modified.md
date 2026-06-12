---
title: "Which time zone is used in the &quot;Last modified&quot; column?"
date: 2016-03-14
forum: General Help
---

### Post by vasa1 on 2016-03-14
When I visit [http://cdimage.ubuntu.com/lubuntu/daily-live/current/?C=M;O=A](http://cdimage.ubuntu.com/lubuntu/daily-live/current/?C=M;O=A), I see the image attached. Can someone please tell me which time zone is being used in the "Last modified" column?

---

### Post by ian-weisser on 2016-03-14
One would imagine UTC or BST or similar. Why?

---

### Post by Habitual on 2016-03-14
```
wget -S 91.189.92.174 | grep Date index.html
```

Date: Mon, 14 Mar 2016 19:24:42 GMT

---

### Post by vasa1 on 2016-03-14
> **Habitual said:**
> ```
wget -S 91.189.92.174 | grep Date index.html
```

Date: Mon, 14 Mar 2016 19:24:42 GMT

Thank you! I had looked at the page's html code in Firefox using ctrl+u and and page info (Alt+t+i): neither gave me the info. But please see the code I posted below.

> **ian-weisser said:**
> One would imagine UTC or BST or similar. Why?
Because I'm using *zsync* to keep my Lubuntu 16.04 iso updated and I'd rather not sync something while it's being updated just as a precaution.


Oops! I just ran the command and this is the output:
```
07:21 AM ~ $ wget -S 91.189.92.174 | grep Date index.html
grep: index.html: **No such file or directory**
--2016-03-15 07:21:36--  http://91.189.92.174/
Connecting to 91.189.92.174:80... connected.
HTTP request sent, awaiting response... 
  HTTP/1.1 200 OK
  Date: Tue, 15 Mar 2016 01:51:36 GMT *<that's just the time I ran the wget command in GMT>*
  Server: Apache/2.2.22 (Ubuntu)
  Last-Modified: Tue, 28 Jul 2015 14:18:14 GMT
  ETag: "b1-51bf0240ba7ea"
  Accept-Ranges: bytes
  Content-Length: 177
  Vary: Accept-Encoding
  Content-Type: text/html
  Connection: keep-alive
Length: 177 [text/html]
Saving to: &#8216;index.html&#8217;

100%[==========================================>] 177         --.-K/s   in 0s      

2016-03-15 07:21:37 (8.42 MB/s) - &#8216;index.html&#8217; saved [177/177]

07:21 AM ~ $ 

```

Edit: I confirmed it's GMT the old-fashioned way. I kept checking the site last night.

---

