---
title: "Problem with clickable window on wayland session"
date: 2023-12-18
forum: General Help
---

### Post by uszczelkapodglowica on 2023-12-18
Hello everyone,


I've been using Ubuntu 22.04.3 for while and am currently facing a challeng with the Electron framework, specifically in the Wayland environment. My goal is to create a window that is clickable and doesnt interfere with the usage of other appplications, something i've successfully achieved in X11 but am struggling with in Wayland

in X11 my setup is as follows: 

let win = new BrowserWindow({
banner: true,
frame: false,
alwaysOnTop: true,
});

win.setIgnoreMouseEvents(true,{forward: true});

This configuration works perfectly in X11, making the window fully clickable without obstructing the use of other applications. However, I havent been able to replicate this functionality in Wayland.

Im wondering if anyone here has experience or insights into achieving a similar effect in Wayland. Is there a specific approach or a set of properties in Electron that work well with Wayland for creating such windows? 

Any advice or suggestions would be greatly appreciated. Im particularly instrested in solutions that have been tested

Thank you in advance for your help!

---

### Post by coffeecat on 2023-12-18
Not development version. *Thread moved to **General Help**.*

---

