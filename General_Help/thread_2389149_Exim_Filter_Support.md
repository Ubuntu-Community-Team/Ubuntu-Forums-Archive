---
title: "Exim Filter Support"
date: 2018-04-12
forum: General Help
---

### Post by ajaykajla on 2018-04-12
[FONT=arial]Hi,


We have following requirement [COLOR=#333333][FONT=&amp]any mail coming from [EMAIL="abc@abc.com"]abc@abc.com[/EMAIL] and subject contains "SomeThing" to go to [EMAIL="xyz@mydomain.com"]xyz@mydomain.com[/EMAIL] with complete headers and to [EMAIL="abc@mydomain.com"]abc@mydomain.com[/EMAIL] without Cc and From headers.[/FONT][/COLOR][/FONT]
[FONT=arial]
[COLOR=#333333][FONT=&amp]I tried following filter but it's removing headers for both [EMAIL="xyz@mydomain.com"]xyz@mydomain.com[/EMAIL] & [EMAIL="abc@mydomain.com"]abc@mydomain.com[/EMAIL]. [/FONT][/COLOR][/FONT]
[FONT=arial][COLOR=#333333][FONT=&amp]
=====[/FONT][/COLOR][/FONT]
[FONT=arial][COLOR=#333333][FONT=&amp]if ("$h_from:" contains "[EMAIL="abc@abc.com"]abc@abc.com[/EMAIL]" and "$header_subject:" contains "SomeThing")[/FONT][/COLOR][/FONT]
[COLOR=#333333][FONT=&amp]then[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]deliver "[EMAIL="xyz@mydomain.com"]xyz@mydomain.com[/EMAIL]" (should go to [EMAIL="xyz@mydomain.com"]xyz@mydomain.com[/EMAIL] With complete headers )[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]endif[/FONT][/COLOR]

[COLOR=#333333][FONT=&amp]if ("$h_from:" contains "[EMAIL="abc@abc.com"]abc@abc.com[/EMAIL]" and "$header_subject:" contains "SomeThing")[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]then[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]headers remove Cc[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]headers remove From[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]deliver "[EMAIL="abc@mydomain.com"]abc@mydomain.com[/EMAIL]" (should go to [EMAIL="abc@mydomain.com"]abc@mydomain.com[/EMAIL] Without Cc and From headers )[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]endif[/FONT][/COLOR]
[COLOR=#333333][FONT=&amp]=====

Please let me know if there is any error in the above code.

Regards,
Ajay[/FONT][/COLOR]

---

