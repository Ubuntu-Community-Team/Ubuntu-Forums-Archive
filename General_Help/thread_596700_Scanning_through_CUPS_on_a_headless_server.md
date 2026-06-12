---
title: "Scanning through CUPS on a headless server?"
date: 2007-10-29
forum: General Help
---

### Post by i.wanna.corndog on 2007-10-29
Here's the deal. I set up CUPS on my headless file server (running Feisty) and printing is working great. I have an Epson CX3800 Printer/Scanner/Copier. My question is simple:  is there any way to set up scanning over the network with CUPS? What I'd really like is the ability to scan a document directly to PDF format and have it delivered to a network folder. If this wouldn't be possible, I wouldn't mind being able to scan to a shared folder on the local drive of the server. Or, I'd like to be able to see the scanner as a network TWAIN scanner.

Would it be at all possible to set something up like this? Also, I'd prefer to run scans over a web-based interface so I wouldn't have to SSL over to the server every time I want to scan.

I feel like this post is a bit scatter brained, so I apologize. Am I asking for too much?

Thanks :)
Dan

---

### Post by MrFSL on 2007-10-30
Network scanning is possible but not through CUPS as far as I know. You would use SANE.

I used the following:
[http://www.linux.com/articles/57798](http://www.linux.com/articles/57798)

To setup my headless network scanner. It was rather easy.

---

