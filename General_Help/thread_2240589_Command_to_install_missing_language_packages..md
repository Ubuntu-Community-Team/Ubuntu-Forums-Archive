---
title: "Command to install missing language packages."
date: 2014-08-21
forum: General Help
---

### Post by negora on 2014-08-21
Hello:

Ubuntu, Xubuntu and other derivatives are able to detect which language packages are missing and prompt the user if he/she wants to install them. If I'm not mistaken, it checks what packages have been installed and then it looks for the corresponding language packs.

I want to know if there's a command, to be executed in console mode only, that it's able to do that. Or do I've to do it by hand?

Thank you.

---

### Post by cj13579 on 2014-08-21
Yes, this is possible. To check what packages are in a language pack you can run:

```
 check-language-support -l {code} 
```

For example, French:

```
chris@q2server:~$ check-language-support -l fr
language-pack-fr language-support-writing-fr 
```

You can then install the french language pack by running:

```
 sudo apt-get install language-pack-fr language-support-writing-fr  
```

---

### Post by slickymaster on 2014-08-21
Auto install required language package and all its dependencies:```
sudo apt-get -y install `check-language-support -l **[COLOR=#ff0000]??[/COLOR]**`
```Replace [COLOR=#ff0000]??[/COLOR] with the 2-letter country codes of the required idiom

---

### Post by negora on 2014-08-21
Hello:

That's exactly what I was looking for!

Thank you both,  cj13579 and slickymaster :) .

---

