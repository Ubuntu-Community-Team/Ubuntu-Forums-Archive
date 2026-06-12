---
title: "Lubuntu Document Web Page Error"
date: 2020-10-30
forum: General Help
---

### Post by tlhcelik on 2020-10-30
Hi, i get an error when i click [docs.lubuntu.net]("http://docs.lubuntu.net"). Can look at this error someone? 

Whoops\Exception\ErrorException thrown with message "Trying to access array offset on value of type null"


Stacktrace:
#14 Whoops\Exception\ErrorException in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1229
#13 Whoops\Run:handleError in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1229
#12 Grav\Common\Page\Pages:buildSort in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:298
#11 Grav\Common\Page\Pages:sort in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1112
#10 Grav\Common\Page\Pages:recurse in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:1077
#9 Grav\Common\Page\Pages:recurse in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:948
#8 Grav\Common\Page\Pages:resetPages in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:928
#7 Grav\Common\Page\Pages:buildPages in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Page/Pages.php:213
#6 Grav\Common\Page\Pages:init in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Processors/PagesProcessor.php:24
#5 Grav\Common\Processors\PagesProcessor:process in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:132
#4 Grav\Common\Grav:Grav\Common\{closure} in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:379
#3 Grav\Common\Grav:Grav\Common\{closure} in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:355
#2 call_user_func_array in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:355
#1 Grav\Common\Grav:__call in /home/lubuntun1/public_html/docs/system/src/Grav/Common/Grav.php:133
#0 Grav\Common\Grav:process in /home/lubuntun1/public_html/docs/index.php:52

---

### Post by CelticWarrior on 2020-10-30
Welcome.

The official website is [www.lubuntu.me](www.lubuntu.me)
Stay away from the .net domain

---

