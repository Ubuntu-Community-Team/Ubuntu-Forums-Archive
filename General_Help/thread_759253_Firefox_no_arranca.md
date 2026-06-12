---
title: "Firefox no arranca"
date: 2008-04-18
forum: General Help
---

### Post by geronimox on 2008-04-18
Buenas Noches..
Bueno, soy nuevo en linux, tengo la version 7.1 Gutsy, la verdad que esta muy buena esta distribucion.
Logre hacer casi todo jeje hasta el wifi, pero llego un problemita que no pude resolver.

Use el firefox un par de veces, pero de repente, se rompio, no se que paso :S
lo corro desde el acceso directo y se queda unos 10 segundos en la barra el cuadrito que dice "Iniciando Navegadro Web Firefox.." y luego se va, pero firefox nunca arranca.
Si lo corro de la consola me da este error.
```
gero@CompaqV3000:~$ firefox
/usr/lib/firefox/firefox-bin: error while loading shared libraries: libplc4.so.0d: wrong ELF class: ELFCLASS32
```
Realmente no se que podria ser.. por eso pido a quien se le ocurra como solucionarlo, postee un mensajito.
Saludos!

---

### Post by Diabolis on 2008-04-19
Revisa que las librerias que quiere utilizar esten correctamente instaladas.
```
sudo apt-get install libplc4.so.0d
```

Tambien puedes checar que no tengas programas mal instalados, ve a:
sistema / administracion / synaptic package manager / edit / fix broken packages

---

