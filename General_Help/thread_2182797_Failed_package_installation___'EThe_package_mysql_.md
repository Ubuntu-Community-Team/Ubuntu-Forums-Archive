---
title: "Failed package installation /  'E:The package mysql needs to be reinstalled, but I ca"
date: 2013-10-22
forum: General Help
---

### Post by mtg3992 on 2013-10-22
While installing MYSql as downloaded from Oracle, my system locked up leaving me with a corrupt installation. Now I am unable to launch the Software center or check for updates. I assume the best course would be to manually remove MySQL (enterprise, fwiw) then reinstall Using the SW Center instead of the newer download from Oracle.

Is this this best solution? If so, how do I go about it? If not, please help!

---

### Post by mtg3992 on 2013-10-22
Found this: [http://askubuntu.com/questions/129307/mysql-package-problem-after-update](http://askubuntu.com/questions/129307/mysql-package-problem-after-update)

sudo dpkg --remove --force-remove-reinstreq mysq[COLOR=#333333][FONT=UbuntuRegular] fixed the problem.[/FONT][/COLOR]

---

