---
title: "Gateway timeout on part of the server"
date: 2018-04-30
forum: General Help
---

### Post by lionelcharles on 2018-04-30
Hello, we use Ubuntu 16.04 along with NGINX and the server runs Node JS for root folder and sub-folder runs PHP. For instance, we have a blog on [https://www.indiafilings.com/learn/ ]("https://www.indiafilings.com/learn/")

Now, sometimes we are getting a gateway time out on the sub-folder but not on the entire site. So how do we ensure that the subfolder running Wordpress doesn't get timeout.

---

### Post by SeijiSensei on 2018-05-01
Is the MySQL database running on the same machine as WP?  What's the normal load average on this machine?

If you access a specific file URI on the site like an image (e.g., /wp-content/uploads/2018/04/mypicture.png), does it still time out?

---

