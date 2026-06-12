---
title: "SSH help."
date: 2013-07-03
forum: General Help
---

### Post by caleb12134 on 2013-07-03
I am having two issues. I get a permission denied publickey and I have a server staff who I want to check up on. he ssh's alot. I want to connect to his ssh session and see what he is doing. thanks!

---

### Post by CaptainMark on 2013-07-03
Well SSH (Secure shell) is just that: secure. You can't just eavesdrop his connection. (Well, it is possible but this is not the place to discuss cracking into someones terminal), so unless you need to know how to setup  a shared shell connection then you're out of luck.

The permission denied public key error means your trying to connect to a computer that has been configured to only allow pre-authorised computers to connect and that you are not pre-authorised

---

### Post by uRock on 2013-07-03
If you are his administrator, then you should have access to the server's log files via your admin account. If you need help with that then please feel free to start a thread asking for help with reading the log files.

We will not help you crack someone else's SSH key.

Thread Closed

---

