---
title: "openssl upgrade for Ubuntu 13.04 - Problem"
date: 2014-04-11
forum: General Help
---

### Post by One_of_Six on 2014-04-11
As Ubuntu server 13.04 is no longer supported, I used a fix which was posted in another forum to update my Ubuntu 13.04 server openssl to 1.0.1g .

It was two command lines

curl [https://www.openssl.org/source/openssl-1.0.1g.tar.gz](https://www.openssl.org/source/openssl-1.0.1g.tar.gz) | tar xz && cd openssl-1.0.1g && sudo ./config && sudo make && sudo make install

and

sudo ln -sf /usr/local/ssl/bin/openssl `which openssl`

It worked great! I now have the latest version of openssl installed  BUT when I go to terminal and log on, there is now only one directory available when I type  the dir command - "openssl-1.0.1g" I cannot see any other directories in my user account or root!

Can anyone help me to see my directory tree again?

Thank you

---

