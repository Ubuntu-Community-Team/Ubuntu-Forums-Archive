---
title: "libmircookie-dev 404 Not Foud"
date: 2018-09-13
forum: General Help
---

### Post by kedan on 2018-09-13
I tried to install SDL_Image2 on Ubuntu 16.04LTS, but apt didn't found required libmircookie package.
Problem lies here: [http://security.ubuntu.com/ubuntu/pool/main/m/mir/libmircookie-dev_0.26.3+16.04.20170605-0ubuntu1.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/m/mir/libmircookie-dev_0.26.3+16.04.20170605-0ubuntu1.1_amd64.deb)
As you see there is little mistake:

> The requested URL  /ubuntu/pool/main/m/mir/libmir**coieok**-dev_0.26.3+16.04.20170605-0ubuntu1.1_amd64.deb  was not found on this server.

Does anyone know what to do about it?

PS. Every single link to libmircookie is broken: [http://security.ubuntu.com/ubuntu/pool/main/m/mir/](http://security.ubuntu.com/ubuntu/pool/main/m/mir/)

---

### Post by mc4man on 2018-09-13
See no issue here at all with the package or any of your links.
Try
sudo apt update
apt-cache policy libmircookie-dev

If not available (0.26.3+16.04.20170605-0ubuntu1.1) then open Software & Updates and switch to a different server.

(- are you using a proxy?

---

### Post by kedan on 2018-09-13
Neither ```
env | grep proxy
``` nor ```
echo $HTTP_PROXY
``` didn't show anything, But It seems that my ISP scramble 'cookie' keyword in every request (when I use other connection everything is ok). This reminds me, that some time ago I had very frustrating problems to get $SERVER_COOKIE data. Still trying to figure this out. 

Edit: 
This behaviour appears only on port 80. I can download ubuntu's lib via ftp and install them manually, but that doesn't solve main problem.

---

