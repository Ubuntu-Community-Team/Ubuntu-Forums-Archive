---
title: "AH00686: cannot read directory for multi: /var/www/mysite/web/"
date: 2022-01-11
forum: General Help
---

### Post by konkoutr on 2022-01-11
[COLOR=#232629][FONT=-apple-system]I have a problem. I have ispconfig and i have a lot of sites. If i make from beginning the joomla installation, the site works fine. When i moved 6 sites from another server, the 3 of them works fine but the other 3 i get an empty page with the word error. I try to search the solution but i didnt find anything. Only that perhaps it must be from apache2/php.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]I see the error log and the error that says there is:[/FONT][/COLOR]
[Mon Jan 10 14:38:08.064460 2022] [negotiation:error] [pid 3501998] (13)Permission denied: [client myip:port] AH00686: cannot read directory for multi: /var/www/mysite/web/

[COLOR=#232629][FONT=-apple-system]I have done some changes to .htaccess and php.ini but neither worked. Also the permissions are the same at the folders that the sites are working and the sites that arent working.[/FONT][/COLOR]
[COLOR=#232629][FONT=-apple-system]Ubuntu version is 20.04.3.

Thank you in advance[/FONT][/COLOR]

---

