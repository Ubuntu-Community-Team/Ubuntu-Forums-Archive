---
title: "Apache sever password?"
date: 2024-03-26
forum: General Help
---

### Post by garyed on 2024-03-26
I'm running an Apache server on Unbuntu 22.04
I did port forwarding so i could access the server remotely & everthing was working fine. 
Then I decided to password protect the server so i used httpasswd & then added some code to the .htacces file.  
Everything seemed to be working fine until I found that 3 out 10 directories gave me an Internal Server Error 500.   
I've checked permissions & there are no differences I could find between the directories that work fine & the ones that give me an error.
I appreciate any ideas

---

### Post by biledk on 2024-03-26
Hi Garyed
Love your signature :)

Can you perhaps get a clue in the /var/log/apache2/error.log
Do you have multiply .htaccess files in these directories?
Perhaps the apache2.conf conflict with your setup?

---

### Post by garyed on 2024-03-26
> **biledk said:**
> Hi Garyed
Love your signature :)

Can you perhaps get a clue in the /var/log/apache2/error.log
Do you have multiply .htaccess files in these directories?
Perhaps the apache2.conf conflict with your setup?

Actually that did the trick & thank you very much. 
When I checked the error log it showed the errors were in my .htaccess files in those directories 
They had the rewrite code needed for https that was needed for my webhost when I added SSL certificates to my site. 
I guess since my Apache server is just "http" & I changed the one .htaccess file in my root directory to add a password, it caused a conflict.

---

### Post by biledk on 2024-04-03
Great to hear Garyed \\:D/

---

