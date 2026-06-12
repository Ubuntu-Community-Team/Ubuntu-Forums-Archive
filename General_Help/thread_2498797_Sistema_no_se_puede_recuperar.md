---
title: "Sistema no se puede recuperar"
date: 2024-06-27
forum: General Help
---

### Post by ryxen on 2024-06-27
Hola con todos, hace 3 días instalé Ubuntu 24.04 y en la personalización quise cambiar el diseño del puntero del mouse, en configuraciones había una opción que decía algo con transparente (no lo recuerdo) pero al elegirlo, el sistema falló y ahora solo me aparece una pantalla blanca con el mensaje "Ocurrió un problema y el sistema no se puede recuperar. Cierre sesión e inténtelo de nuevo". 

Al apagarla y encenderla,  inicia todo correcto, hasta me muestra el login y me permite acceder pero luego de eso me vuelve a mostrar la misma pantalla. 

Seguro se soluciona volviendo a cambiar el puntero, pero cómo lo puedo hacer?

---

### Post by ryxen on 2024-06-27
Bueno! he podido solucionar el problema, el puntero que me dió dicho error es Whiteglass. Lo que hice fué ingresar al sistema sin interfaz, encendí el ordenador y en la pantalla de login usé ctrl + alt + f3, luego usé el comando gsettings set org.gnome.desktop.interface cursor-theme 'Adwaita'. Luego de eso he reiniciado el computador y el error ha desaparecido.

---

