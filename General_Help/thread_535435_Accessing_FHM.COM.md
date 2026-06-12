---
title: "Accessing FHM.COM"
date: 2007-08-26
forum: General Help
---

### Post by DistantDave on 2007-08-26
It's not the most crucial website in the world - but is the problem mine, or theirs?

I suspect the latter - I can get to the site using Windows on this PC, and also on anothe RPC on the same router, but on neither via Konqueror.

I am using Feisty on this machine, and Dapper on the other.

Also, if I ping fhm.com I get either 

195.69.153.20
or
204.74.99.100

alternately, which is extreemely odd.

Anyone else having any problems at all ?


Cheers

---

### Post by jclmusic on 2007-08-26
could it be that ur lacking some plug-ins that the website uses?

---

### Post by kellemes on 2007-08-26
No problem viewing the site on my end.
What's going wrong then?

---

### Post by por100pre1 on 2007-08-26
No problems here. Any problem with a particular section or the whole page?

---

### Post by Vorian on 2007-08-27
let's not make this an excuse thread to link to everyones favorite mens magazine.  The OP has a legitimate problem, stick to that.

:)

---

### Post by AlexThomson_NZ on 2007-08-28
That's pretty vague.  Does the browser show anything, or just time out?

Can you telnet to that site on port 80?

If so, can you do a HTTP get?

(In Telnet)
```

GET / HTTP/1.1
Host: www.fhm.com
<press enter twice>

```

---

### Post by finer recliner on 2007-08-28
> **AlexThomson_NZ said:**
> That's pretty vague.  Does the browser show anything, or just time out?

Can you telnet to that site on port 80?

If so, can you do a HTTP get?

(In Telnet)
```

GET / HTTP/1.1
Host: www.fhm.com
<press enter twice>

```

```

$telnet 195.69.153.20 80
Trying 195.69.153.20...
Connected to 195.69.153.20.
Escape character is '^]'.
GET / HTTP/1.1
Host: www.fhm.com

HTTP/1.1 302 Found
Date: Tue, 28 Aug 2007 04:49:03 GMT
Server: Microsoft-IIS/6.0
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50727
Location: /Site/NewHome.aspx
Set-Cookie: ASP.NET_SessionId=q5kcffm2w5vwx5usmbfmcq55; path=/; HttpOnly
Cache-Control: private
Content-Type: text/html; charset=utf-8
Content-Length: 135

<html><head><title>Object moved</title></head><body>
<h2>Object moved to <a href="/Site/NewHome.aspx">here</a>.</h2>
</body></html>



```

---

