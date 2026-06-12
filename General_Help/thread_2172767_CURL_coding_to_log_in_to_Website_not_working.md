---
title: "CURL coding to log in to Website not working"
date: 2013-09-06
forum: General Help
---

### Post by s_pal2 on 2013-09-06
Hi, 
I am trying to automate a flight searching on British Airways (url: [https://www.britishairways.com/travel/redeem/execclub/_gf/en_gb](https://www.britishairways.com/travel/redeem/execclub/_gf/en_gb) )
For logging into the website I am trying the following code

curl -A "Mozilla/4.73 [en] (X11; U; Linux 2.2.15 i686)" \
--cookie cjar --cookie-jar cjar \
--data "Directional_Login=/travel/loginr/execclub/_gf/en_gb?eId=109004" \
--data "password=<my pwd>" \
--data "membershipNumber=<my usr>" \
--data "loginButton=1" \
--referer "www.britishairways.com/travel/loginr/execclub/_gf/en_gb" \
--location "www.britishairways.com/travel/loginr/public/en_gb?eId=109001"|w3m -dump -T text/html

But the code is not actually getting me past the log in page, it's returning to the same log in page BUT WITHOUT ERROR. Note: The action for LOGIN button is defined as "OnClick" in the html code of the website. I am guessing I am not able to pass that action in CURL. Any help would be much appreciated.

---

