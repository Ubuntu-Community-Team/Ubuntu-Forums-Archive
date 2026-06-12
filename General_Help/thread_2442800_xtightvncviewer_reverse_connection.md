---
title: "xtightvncviewer reverse connection"
date: 2020-05-07
forum: General Help
---

### Post by marcw on 2020-05-07
I can tell the old vncviewer to perform a reverse connection on any old port with a simple:
vncviewer -listen 5501

But I want to use xtightvncviewer instead because it works better and much faster.  However the man page for xtightvncviewer says that it only listens on port 5500.  Is there a way to use a reverse connection with xtightvncviewer on ports other than 5500?

---

### Post by DuckHook on 2020-05-07
I don't know the answer to your question. However, if you are doing VNC in the clear over an unencrypted Internet connection, you are already juggling with live hand grenades.

VNC is a terrible, awful protocol. It is a primary source of thousands of people getting pwned. If you want a real scare, just examine your logs no matter which port you use. If you simply *must* use it, then the highly recommended&#8212;I would even go so far as to say, the *only* proper way&#8212;is to tunnel it through a secure protocol like SSH, with passwords disabled entirely and the connection made only using public/private paired keys. If you do that, then it doesn't matter what port VNC uses.

Instructions can be found with a simple web search. Typical instructions here: [https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/](https://www.techrepublic.com/article/how-to-connect-to-vnc-using-ssh/)

---

