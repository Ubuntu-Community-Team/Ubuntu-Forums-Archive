---
title: "PHP 5.5.9 Cannot redeclare class"
date: 2014-10-06
forum: General Help
---

### Post by waynehulls on 2014-10-06
[COLOR=#333333][FONT=Lucida Grande]After a UBUNTU update (including to PHP 5.5.9-1ubuntu4) I received this message[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]"Cannot redeclare class reportico_criteria_column in /data/www/cash_book/reportico/reportico.php on line 5762"[/FONT][/COLOR]

[SIZE=4][I][B][COLOR=#333333][FONT=Lucida Grande]Google searches lead me to an apparent issue with PHP 5.5.9 where parent classes must be declared before extended classes ![/FONT][/COLOR]
[/B][/I][/SIZE]
[COLOR=#333333][FONT=Lucida Grande]So I downloaded the latest Reportico version (Sourceforge file dated 2014-09-05) and in reportico.php moved class reportico_criteria_column (NB extends reportico_query_column)[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]to below class reportico_query_column (NB extends reportico_object)[/FONT][/COLOR]

[COLOR=#333333][FONT=Lucida Grande]Problem solved !!![/FONT][/COLOR]

---

