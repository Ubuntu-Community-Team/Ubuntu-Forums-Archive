---
title: "[SOLVED] Adding Users to Postfix"
date: 2007-10-13
forum: General Help
---

### Post by btaylor101 on 2007-10-13
I have completed the install of Postfix, but had questions on the use of it. I wasn't sure how to add users to postfix and have them be able to check their mail using Thunderbird. I have registered my domain name and it can be seen by the outside world. How do i add a user then have them use Thunderbird to check their mail? How do i tell users what settings to use when creating their accounts?

---

### Post by posterboy on 2007-10-14
Postfix will find them without you doing anything. However, if your users are remote, you will also need to run, for example, a pop3 server. They set up with your domain name as the server and tell t-bird the protocol is pop, and away it will go. This will necessarily open port 110 which you will need to pass through the firewall. Note that this IS a security risk, blackhats will be able to get the user names of accounts on your box. Then a dictionary attack on the password, well, you know the rest. 
There are ways to mitigate this, I'll leave that to others.

---

