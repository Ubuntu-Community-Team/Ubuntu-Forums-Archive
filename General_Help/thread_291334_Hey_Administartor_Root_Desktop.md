---
title: "Hey Administartor Root Desktop"
date: 2006-11-02
forum: General Help
---

### Post by Lukasz Tarkowski on 2006-11-02
Hey evryone
Does anyone know how I can access the root user through desktop cuase it said root cannot access this login form?
When I click logout my screen goes blank, well it goes wild and I have to shutdown my computer.

---

### Post by taurus on 2006-11-02
You run those commands with sudo...  If you need to reconfigure your X again, try it from a terminal with

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by PriceChild on 2006-11-02
The root account is disabled in ubuntu for security reasons.

Read [http://wiki.ubunu.com/RootSudo](http://wiki.ubunu.com/RootSudo) for reasons why, and how to use sudo.



[CENTER]**[COLOR=Red]CODE BELOW IS NOT RECCOMENDED[/COLOR]**
[/CENTER]
 If you really want to....
```
sudo passwd root
```then you can use it.

---

### Post by telepheedian on 2006-11-02
In ubuntu, there is no specific "root" account. Instead, use sudo to execute a command as root.

---

### Post by Ramses de Norre on 2006-11-02
Login into X is possible without setting the password too, press ctrl-alt-F1, log in and do
```
sudo /etc/init.d/gdm stop
sudo startx
```
If you only want to use one program you can start it with sudo (cli) or gksudo (gui).

---

