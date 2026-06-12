---
title: "Move Files"
date: 2013-03-14
forum: General Help
---

### Post by shaquille110 on 2013-03-14
Hi there.

I'm using Ubuntu 12.04 LTS server edition. I'm trying to figure out how to move files from inside the folder /var/www/www/ to /var/www/ and delete the extra /www/ folder. I have tried "sudo mv /var/www/www/ /var/www/' and it doesn't seem to be working.

Please note I am operating Ubuntu via SSH!

Thanks

Overview
Move files from /var/www/www/ to /var/www/ and delete /var/www/www/ folder

---

### Post by steeldriver on 2013-03-14
The way the 'mv' command works, that will actually try to *rename* the /var/www/www directory to /var/www - which it obviously can't since the parent directory alredy exists (and is not empty)

Instead, you want to move the *contents* of /var/www/www up to /var/www 

```
sudo mv /var/www/www/* /var/www/
```

and then [optionally] you can remove the now empty child dir

```
sudo rmdir /var/www/www
```

---

