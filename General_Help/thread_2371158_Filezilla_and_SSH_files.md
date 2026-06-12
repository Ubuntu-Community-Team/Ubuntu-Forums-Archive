---
title: "Filezilla and SSH files"
date: 2017-09-11
forum: General Help
---

### Post by littlemonkey2 on 2017-09-11
I use PuTTy to connect to my server and as I was trying to install node.js I tried: ```
sudo nano app.js
``` to copy paste this from their about as stated: 
```
const http = require('http');

const hostname = '127.0.0.1';
const port = 3000;

const server = http.createServer((req, res) => {
  res.statusCode = 200;
  res.setHeader('Content-Type', 'text/plain');
  res.end('Hello World\n');
});

server.listen(port, hostname, () => {
  console.log(`Server running at http://${hostname}:${port}/`);
});
```

It all worked marvelous but when I went to view/edit the file through filezilla I noticed the notepad++ was empty but it did show the filesize was 340 which made sense, should I write it in there too or just leave it as it is?

---

### Post by TheFu on 2017-09-16
Sorry, but I have no idea what the question is.

Really, life is much easier if you use Linux to access Linux as a developer.  It really is.  X/Windows is an amazing development environment.  The entire OS is designed for developers, unlike Windows.  [https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/](https://sanctum.geek.nz/arabesque/unix-as-ide-introduction/) tries to explain this concept.  Dev tools are already on your Linux machines, waiting to be used.

---

