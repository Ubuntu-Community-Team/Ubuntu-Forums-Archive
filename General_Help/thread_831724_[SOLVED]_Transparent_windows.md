---
title: "[SOLVED] Transparent windows"
date: 2008-06-17
forum: General Help
---

### Post by kismeras on 2008-06-17
Hello all, 

I am extremely new to Ubuntu/Linux and i need some help. When i say new, i mean you have to explain things to me in the simplest way possible. I'm just now learning to use the terminal, etc, etc.

Here is my question. I have seen screen shots where people are using "the cube" and some where people have transparent windows. 

Is there a step by step guide to getting the cube and installing it for dummies? Also, is there a similar guide for getting the transparent windows? I was able to make my panel bar transparent and the windows title bar too, but not the whole window. 

Also, i did search, but i could not find anything i could understand. Thanks.

---

### Post by easybake on 2008-06-17
[http://ubuntuforums.org/showthread.php?t=809695&highlight=install+compiz+fusion](http://ubuntuforums.org/showthread.php?t=809695&highlight=install+compiz+fusion)

Do the steps in 'how do i know if compiz is enabled'

Also 'what is a quicker way...'

and 'Simple CompizConfig Settings Manager doesn't provide enough options or effects'

follow those steps. They'll mention the terminal a lot. Which is located in Accessories>Terminal.

---

### Post by attari on 2008-06-17
> **kismeras said:**
> Hello all, 

I am extremely new to Ubuntu/Linux and i need some help. When i say new, i mean you have to explain things to me in the simplest way possible. I'm just now learning to use the terminal, etc, etc.

Here is my question. I have seen screen shots where people are using "the cube" and some where people have transparent windows. 

Is there a step by step guide to getting the cube and installing it for dummies? Also, is there a similar guide for getting the transparent windows? I was able to make my panel bar transparent and the windows title bar too, but not the whole window. 

Also, i did search, but i could not find anything i could understand. Thanks.


You might wanna follow this customization guide here:
[http://www.attari.net/index.php?My_space...:Customizing_Ubuntu]("http://www.attari.net/index.php?My_space...:Customizing_Ubuntu")

You can also get some cool apps here:
[http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications]("http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications")

Regarding the cube... you need 'compiz' and 'compizconfig-settings-manager' . Install them from synaptic package manager. compiz should already be there, you would need to install the other package. Next go to Menu> System > Preferences> Advanced Desktop Effects Setting. There enable the cube and tweek the settings to your choice.

Regarding the transparent window just press:
Alt + Mouse scroll up: Increase opacity in the active window.
Alt + Mouse scroll down: Decrease opacity in the active window.

(Note: this transparency is only affects the active window until its closed. When the window is closed its reset to default. 

To change the defaults go to: Menu> System> Prefrences> Advanced Desktop Effects Settings. In the CompizConfig Settings Manager window go to General Options, then Opacity Settings. Press Add button, type this into the box: type=normal. Set the opacity between 30 - 99 if you want translucent windows that you can still see, set it above 100 and it will be greater than opaque (it will be SUPEROPAQUE!), set it under 30 or so, and you won't really be able to see the windows too well, not even the one to change the setting back!)

---

### Post by kismeras on 2008-06-17
Man, you guys are awesome. Thanks to both of you. I now have the cube installed and configured as well as the AWN Dock and transparent windows. Thanks a million.

---

### Post by kismeras on 2008-06-18
Hey Guys, 

How do i get the AWD dock to the top of the screen? Right now it is at the bottom, but I would prefer it on top. Thanks.

---

### Post by easybake on 2008-06-18
AWN doesn't have that yet. Think they'll try have that for 0.3 release.

In terminal type ```
metacity --replace
``` to stop using compiz if you mess something up.

---

### Post by kismeras on 2008-06-18
Awesome, thank you. The problem is i could not see any window, so i would not know where i was typing. I turned my brightness all the way down and i'm not sure what else i did, but i was able to barely see the window. That allowed me to change it to something better...90 right now.

---

### Post by saratchandra on 2008-06-19
> **kismeras said:**
> Hey Guys, 

How do i get the AWD dock to the top of the screen? Right now it is at the bottom, but I would prefer it on top. Thanks.

You can't, with AWN. Try cairo-dock instead.

---

### Post by kismeras on 2008-06-19
Thanks. I'll try that today.

---

