---
title: "phpmyadmin extension error"
date: 2017-04-24
forum: General Help
---

### Post by sniper8752 on 2017-04-24
After I install phpmyadmin, I get this error:
```
The mbstring extension is missing. Please check your PHP configuration[COLOR=#000000][FONT=sans-serif].[/FONT][/COLOR]
```

MBstring is already installed.

---

### Post by SeijiSensei on 2017-04-24
Create a php script with the single line
```
<?php phpinfo() ?>
```
then view it from a browser.  Does the mbstring stanza appear with "Multibyte Support enabled?"

---

### Post by sniper8752 on 2017-04-24
I can't find mbstring in there.

---

### Post by sniper8752 on 2017-04-26
*bump*

---

### Post by dragonfly41 on 2017-04-27
This thread might help you .. but I suggest that in future posts you give more information on your configuration ..

Ubuntu version, php version etc. .. otherwise readers are guessing.

[https://askubuntu.com/questions/772397/mbstring-is-missing-for-phpmyadmin-in-ubuntu-16-04](https://askubuntu.com/questions/772397/mbstring-is-missing-for-phpmyadmin-in-ubuntu-16-04)

---

