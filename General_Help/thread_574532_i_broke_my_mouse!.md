---
title: "i broke my mouse!"
date: 2007-10-12
forum: General Help
---

### Post by ninjaprawn on 2007-10-12
i have a m$ intelimouse which is 7 buttons, it was working perfectly in firefox for ages after i set the xorg.conf file to use the side buttons to navigate back and forward, suddenly, theyve started scrolling the page horizontaly!

i checked my xorg.conf, nothings changed! its like the browser is doing the wrong thing suddenly! how can i change this? i have recently created a user.js file to optimise ff, and the problem started as soon as i had, so i just removed the file, restarted x, and still the same!

help!

thanks.

---

### Post by ninjaprawn on 2007-10-12
sorry! ignore me, i fixed it! the user.js file must have modified about:config, the line;-
mousewheel.horizscroll.withnokey.action
had been changed to 2 insted of 1!

---

