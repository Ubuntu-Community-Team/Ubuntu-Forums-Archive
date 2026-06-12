---
title: "Mime Type Issue Driving Me Crazy!"
date: 2007-08-10
forum: General Help
---

### Post by mareltrout on 2007-08-10
I have several ColdFusion file upload apps running on Ubuntu, and about 2 weeks ago we upgraded to Feisty Fawn and the latest version of Apache2. All my CF file upload apps continue to work fine except when it comes to xls files. I've checked directory permissions: they are correct. I've doublechecked the mime type in my CF app: **application/vnd.ms-excel**, which is correct and matches the mime type listed in **/etc/mime.types**. I've checked the file path in my CF app: it is correct. And yet xls files refuse to upload. The only way I can get an xls to upload is to do something insane like change the mime type in my CF app to **application/***. Can anybody tell me wtf is going on?

---

