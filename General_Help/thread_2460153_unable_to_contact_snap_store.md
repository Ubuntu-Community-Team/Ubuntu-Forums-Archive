---
title: "unable to contact snap store"
date: 2021-04-03
forum: General Help
---

### Post by davoudi on 2021-04-03
So I recently switch from Linux Mint 20 to Ubuntu 20.04 LTS because I receive the error (unable to contact snap store) whenever I wanted to install a software via snap. Fortunately snap store works fine on my laptop but not my desktop (I receive the same error) so I was wondering if you could provide any solution.

 Thanks in advance for your time.

---

### Post by grahammechanical on 2021-04-03
It is not clear if you are unable to connect to the snap store in Ubuntu 20.04 or Linux Mint 20. Did you do a fresh install of Ubuntu 20.04? It is my understanding that the Linux Mint developers have deliberately made it impossible to install and run snap packaged apps in Linux Mint. You have to make some changes to remove what the Linux Mint developers have done.

[https://snapcraft.io/install/snap-store/mint](https://snapcraft.io/install/snap-store/mint)

Regards

---

### Post by davoudi on 2021-04-03
> **grahammechanical said:**
> 
It is not clear if you are unable to connect to the snap store in Ubuntu 20.04 or Linux Mint 20. Did you do a fresh install of Ubuntu 20.04? It is my understanding that the Linux Mint developers have deliberately made it impossible to install and run snap packaged apps in Linux Mint. You have to make some changes to remove what the Linux Mint developers have done.

[https://snapcraft.io/install/snap-store/mint](https://snapcraft.io/install/snap-store/mint)

Regards

 I install a fresh Ubuntu 20.04 LTS. I was aware that change has to be made in Linux Mint in order to use snap.

---

### Post by TheFu on 2021-04-03
Linux Mint doesn't make it impossible to use snaps.  They just don't setup their system to force snap package use onto administrators/users.  Basically, the snap subsystem has to be installed.  I bet there is a .deb file for it.

```
sudo rm /etc/apt/preferences.d/nosnap.pref
sudo apt update
sudo apt install snapd
```
Yep. A normal apt install. If you want a GUI ... install that package too. Snaps are useful for many things and terrible for some systems.

The "Snap Store" isn't required to use snaps.  They can be installed from a shell/CLI interface. The commands are very similar to those for **apt**.

```
sudo apt install {package name}
sudo snap install {package name}
sudo apt remove {package name}
sudo snap remove {package name}
sudo apt search {package name}
sudo snap search {package name}
```

Very similar.

---

### Post by davoudi on 2021-04-03
> **TheFu said:**
> Linux Mint doesn't make it impossible to use snaps.  They just don't setup their system to force snap package use onto administrators/users.  Basically, the snap subsystem has to be installed.  I bet there is a .deb file for it.

```
sudo rm /etc/apt/preferences.d/nosnap.pref
sudo apt update
sudo apt install snapd
```
Yep. A normal apt install. If you want a GUI ... install that package too. Snaps are useful for many things and terrible for some systems.

The "Snap Store" isn't required to use snaps.  They can be installed from a shell/CLI interface. The commands are very similar to those for **apt**.

```
sudo apt install {package name}
sudo snap install {package name}
sudo apt remove {package name}
sudo snap remove {package name}
sudo apt search {package name}
sudo snap search {package name}
```

Very similar.
 Oh thanks. I was aware of these commands. My problem is that I receive an error (unable to contact snap store) whenever I try to install or search a package.

---

### Post by TheFu on 2021-04-03
> **davoudi said:**
> Oh thanks. I was aware of these commands. My problem is that I receive an error (unable to contact snap store) whenever I try to install or search a package.

[LIST]
[*]What URL is being used?  
[*]Can you go there with a normal browser?  
[*]Can you ping the server by name?  
[*]Ping by IP?
[*]It could be that the server is down or that your part of the world can't reach it.  Use one of the "down for me?" websites to see what other parts of the world see from their location.
[/LIST]

---

### Post by davoudi on 2021-04-03
> **TheFu said:**
> 
[LIST]
[*]What URL is being used?
[/LIST]

 I don't use any URL. I simply run the command sudo snap install package-name.

> **TheFu said:**
> 

[LIST]
[*]Can you go there with a normal browser?
[/LIST]

 Do you mean [FONT=Ubuntu] [/FONT][api.snapcraft.io]("http://api.snapcraft.io/")? I can go there and I get "[COLOR=#000000][FONT=&quot]snapcraft.io store API service - Copyright 2018-2019 Canonical.[/FONT][/COLOR]".

> **TheFu said:**
> 

[LIST]
[*]Can you ping the server by name?
[/LIST]

 Yes.

> **TheFu said:**
> 

[LIST]
[*]Ping by IP?
[/LIST]

 Yes.

> **TheFu said:**
> 

[LIST]
[*]It could be that the server is down or that your part of the world can't reach it.  Use one of the "down for me?" websites to see what other parts of the world see from their location.
[/LIST]

 I don't think that the server is down. I can ping it so it means I can reach it from my country. I was able to install hello-world from my laptop but nothing from my desktop.

---

