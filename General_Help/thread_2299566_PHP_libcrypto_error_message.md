---
title: "PHP libcrypto error message"
date: 2015-10-19
forum: General Help
---

### Post by w-a-u on 2015-10-19
I've had this issue for several weeks and cannot seem to find the answer on the Internet. PHP gives me the following error when attempting to run it via command line:

php: /lib/x86_64-linux-gnu/libcrypto.so.1.0.0: no version information available (required by php)
php: /lib/x86_64-linux-gnu/libcrypto.so.1.0.0: no version information available (required by /lib/x86_64-linux-gnu/libssl.so.1.0.0)
php: /lib/x86_64-linux-gnu/libcrypto.so.1.0.0: no version information available (required by /lib/x86_64-linux-gnu/libssl.so.1.0.0)
php: /lib/x86_64-linux-gnu/libcrypto.so.1.0.0: no version information available (required by /lib/x86_64-linux-gnu/libssl.so.1.0.0)

Not sure what it means or how to solve it. Can anybody steer me in the right direction?

THanks,
Adam

---

### Post by SeijiSensei on 2015-10-19
A [Google search for that error string](https://www.google.com/search?q=libcrypto.so.1.0.0%3A+no+version+information+available) brings up discussions where people are using self-compiled versions of OpenSSL.  Are you using the versions in the repositories?

What version of Ubuntu are you running?

---

