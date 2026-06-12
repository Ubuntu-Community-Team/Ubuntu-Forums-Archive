---
title: "Autohotkey for ubuntu (17.10 Gnome Wayland)"
date: 2017-11-19
forum: General Help
---

### Post by jarvo2 on 2017-11-19
Hi, what is the best application for autohotkey in ubuntu? Bash scripts are something which I sure do use alot but they limit me alot. 
I'd use autohotkey for instance in gimp find a specific colour from the screen, move the cursor over it and double click it. If that's possible with bash script then by all means let me know.

Any help is appreciated. 

-Joonas

---

### Post by Holger_Gehrke on 2017-11-19
The example you picked is not all that good since gimp has at least two macro languages (python and the scheme-like script-fu) and can take commands on the command line, so you could write a macro and call it from a script.

For the more general case of automating a gui application there's xdotool, autokey and autokey py3. Whether these work with Wayland I can't tell you, but I have my doubts, since they are all using very specific extensions of X11. Found them on alternativeto.net , which also mentions sikuli, but that seems to a) be dead and b) have a completely different approach, as it was mainly a research project in using image recognition for task automation.

Holger

---

### Post by dragonfly41 on 2017-11-20
I suggest that you try out Actiona which is in Ubuntu 16.04 Software Centre (although I don't know if it is in 17.04).

---

### Post by vasa1 on 2017-11-20
> **dragonfly41 said:**
> I suggest that you try out Actiona which is in Ubuntu 16.04 Software Centre (although I don't know if it is in 17.04).It seems it is in 17.04 and 17.10: [http://manpages.ubuntu.com/manpages/artful/en/man1/actiona.1.html](http://manpages.ubuntu.com/manpages/artful/en/man1/actiona.1.html)

---

### Post by dragonfly41 on 2017-11-20
I should add that for your specific task if you are looking for specific colours you can create small screenshot areas
which are used in the Find Image component in Actiona.

If you have imagemagick installed you can use the command

```
import screenarea.png
```

to create area of screen to grab as target tor Actiona .. "image to search for" field [...]

Reference: [https://askubuntu.com/questions/18867/which-tool-to-crop-a-portion-of-the-screen](https://askubuntu.com/questions/18867/which-tool-to-crop-a-portion-of-the-screen)

---

### Post by vasa1 on 2017-11-20
It's going to be informative to read OP's response in view of Holger_Gehrke's concern about whether these tools will function in Wayland, which is what OP has mentioned in the thread title.

---

### Post by jarvo2 on 2017-11-22
> **Holger_Gehrke said:**
> The example you picked is not all that good since gimp has at least two macro languages (python and the scheme-like script-fu) and can take commands on the command line, so you could write a macro and call it from a script. 

Yes indeed it was a bad example. Couldn't figure out a more reasonable one to explain.

> **Holger_Gehrke said:**
> 
For the more general case of automating a gui application there's xdotool, autokey and autokey py3.

You were right, xdotool does not work properly with wayland. I have yet to try autokey and autokey py3, but I'll edit this post section as soon as I've tested them, but I have a feeling they don't work properly.

> **dragonfly41 said:**
> 
If you have imagemagick installed you can use the command
```
import screenarea.png
```

 **Imagemagic** does not work with wayland. Actiona is unable to scan the screen (Wayland prevents applications for doing that I believe). I'm guessing  I could make a script that uses gnome-screenshot tool to take a screenshot and scan the screenshot for specific pixel colour location but **I don't know how to scan the taken 1920x1080 picture of my desktop and find a specific pixel coordinates from it.  **I could then import the location of the specific coordinate to Actionaz. If someone can help me with this I would be grateful.  

I can move the mouse around the screen with Actiona and emulate keypresses correctly, but **I'm unable to simulate keypresses such as <alt>f11**. The script simulates the keypress but not on enough high system -level as pressing the key combinations manually.

---

### Post by dragonfly41 on 2017-11-22
I am on Ubuntu 16.04 and have no experience with Wayland.

However I read this ..

[https://support.hubstaff.com/screenshot-capture-support-wayland-linux/](https://support.hubstaff.com/screenshot-capture-support-wayland-linux/)

which suggests switching back to xorg while screen shots are taken.

[https://support.hubstaff.com/screenshot-capture-support-wayland-linux/](https://support.hubstaff.com/screenshot-capture-support-wayland-linux/)

Is that a work around?

Also this related post ...

[http://www.omgubuntu.co.uk/2017/09/install-shutter-0-94-on-ubuntu](http://www.omgubuntu.co.uk/2017/09/install-shutter-0-94-on-ubuntu)

---

