---
title: "How to enable XPM library  in gd?"
date: 2013-02-01
forum: General Help
---

### Post by pcrio2 on 2013-02-01
Hello, i installed php with gd library, but when i check php.ini files it doesnt show the xpm and xbm libraries, id like to know how do i enable these extensions. Because i need to insert Captcha in my website.

Ps: i installed libxpm-dev and libxpm through apt-get install command. And nothing changed in php.ini.

Link: [http://www.pergunteaoprofissional.com.br/gd.php](http://www.pergunteaoprofissional.com.br/gd.php)

Regards,

Paulo Menezes

---

### Post by slickymaster on 2013-02-01
You enable support for xpm by specifying the --with-XXXX configure switch to your PHP configure line. Just add **--with-xpm-dir=DIR**. If configure is not able to find the required libraries, you may add the path to your X11 libraries.

DIR is the GD base install directory.

---

### Post by pcrio2 on 2013-02-01
Hello, i installed php with gd library, but when i check php.ini files  it doesnt show the xpm and xbm libraries, id like to know how do i  enable these extensions. Because i need to insert Captcha in my website.

Ps: i installed libxpm-dev and libxpm through apt-get install command. And nothing changed in php.ini.

Link: [http://www.pergunteaoprofissional.com.br/gd.php](http://www.pergunteaoprofissional.com.br/gd.php)

Regards,

Paulo Menezes

---

### Post by pcrio2 on 2013-02-01
> **slickymaster said:**
> You enable support for xpm by specifying the --with-XXXX configure switch to your PHP configure line. Just add **--with-xpm-dir=DIR**. If configure is not able to find the required libraries, you may add the path to your X11 libraries.

DIR is the GD base install directory.

In very new in linux platform, can you tell me where can i find this directory?

---

### Post by pcrio2 on 2013-02-01
I noticed you are from POrtugal, im from Brasil, maybe its easier talking in portuguese if you agree.

> **slickymaster said:**
> You enable support for xpm by specifying the --with-XXXX configure switch to your PHP configure line. Just add **--with-xpm-dir=DIR**. If configure is not able to find the required libraries, you may add the path to your X11 libraries.

DIR is the GD base install directory.

---

### Post by slickymaster on 2013-02-01
Tudo bem, Paulo. Assim será mais imediato.

O que tens de fazer é passar o parâmetro usando --with-gd = "Caminho", em que "Caminho" é o local (caminho/path para a pasta) onde está a biblioteca.

Para saberes onde a biblioteca está, basta abrires uma janela/terminal e correres os seguintes comandos:
```
cd /
find -name *versão da tua libgd*
```

Espero ter ajudado e que consigas resolver o teu problema.

Abraço.

---

### Post by slickymaster on 2013-02-01
Se precisares de referências, dá uma vista de olhos ao [manual de instalação]("http://www.php.net/manual/pt_BR/image.installation.php"). O idioma está em pt_BR.

Boa sorte.

---

### Post by pcrio2 on 2013-02-02
Hello, i want to enable XPM Support to php5-gd , and i know i have to put **--with-xpm-dir=DIR **somewhere i dont know. What file should i edit to insert this command.

GD.php:[http://www.pergunteaoprofissional.com.br/gd.php](http://www.pergunteaoprofissional.com.br/gd.php)

Thank You :D

---

### Post by howefield on 2013-02-02
Threads merged, please keep to one thread per issue, make it easier on anyone trying to help you.

---

