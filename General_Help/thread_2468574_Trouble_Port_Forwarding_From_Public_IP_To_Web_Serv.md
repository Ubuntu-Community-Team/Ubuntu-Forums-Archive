---
title: "Trouble Port Forwarding From Public IP To Web Server Using Domain Name"
date: 2021-11-03
forum: General Help
---

### Post by turtley-linux on 2021-11-03
Hello,
I recently bought a domain name, but unfortunately, I am having trouble getting the domain name to forward to the web server, especially after setting up https encryption with certbot. It worked before adding the https encryption both in and out of the home network. When I open the webpage now from my home network (the server is on the home network) I am redirected to the router settings webpage. When I type in the public IP address, it takes me to the Apache default page, not the website. When I am not at home, it doesn't work at all. I am using a virtual host and Ubuntu Server 21.04. Please see the router port forward settings and virtual host setup. I have tried looking for any information on this but have been stumped for a few weeks.
I appreciate your help, have a good day!

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289421&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=289422&stc=1[/IMG]

---

### Post by Doug S on 2021-11-03
Your external IP address is redirecting from any attempts on port 80 to port 443, as per your rewrite rules. However, anything on port 443 never gets any response. You need to port forward port 443 also.

---

### Post by turtley-linux on 2021-11-03
Wow, it works perfectly! Thank you for your help, @Doug S!

---

### Post by Doug S on 2021-11-04
Glad you got it fixed. Interesting web site.

By the way, typo: "liquid damage reapir"

---

