---
title: "Random SSL errors"
date: 2008-03-17
forum: General Help
---

### Post by whompar on 2008-03-17
Hi,

I have some strange SSL errors using ubutu 7.10.

Some websites will work with SSL while others will not. For example [https://www.amazon.co.uk](https://www.amazon.co.uk) will connect while [https://www.amazon.com](https://www.amazon.com) will not.

If I use openssl s_client -connect amazon.co.uk:443, this connects ok. However if I use
openssl s_client -connect amazon.com:443, I get the following error...

connect: Connection refused
connect:errno=29

Could openssl be set up to only validate UK registered certs ? Or anyone have any ideas ?

Thanks.

Please ignore this...

---

