---
title: "AMD HD5xxx, ext monitor, extreme lag unless I disable and re-enable built-in display"
date: 2017-02-23
forum: General Help
---

### Post by ULAMSS5 on 2017-02-23
Hi All!

I have recently replaced Windows with Ubuntu 16.10 on an ancient laptop my friend passed to me.

It has a HDMI out, which I'm using to connect to an external display (LG 25UM58-P), which is 21x9 but I can't set it beyond 16:9,  but that is for another thread.

Using an old gpu that shows up as HD 5xxx/6xxxm, with open-source radeon drivers.

Right now the laptop is EXTREMELY SLOW unless I disable and re-enable the built-in display. It is also extremely slow if I disable the built-in display altogether, which would be ideal since it's under the desk and just powering the monitor and kb/m. When it's lagging, the mouse moves very smoothly, any inputs are properly registered, but everything takes like 1 minute to move or change. Especially noticeable with Unity UI transparency stuff fading in and out, or opening and closing any windows, or typing into the Terminal. It feels like the system is clocked at 1Hz.

So right now I have to take 10 minutes to open and fiddle with the Screen Display after each logon.

Are there any more permanent solutions to this? Any help would be greatly appreciated :)

---

### Post by DuckHook on 2017-02-23
The phrase "ancient laptop" combined with "Ubuntu" and "Unity UI transparency" does nothing but ring alarm bells.

[LIST=1]
[*]Both Ubuntu and Kubuntu are meant for modern HW with fast CPUs, lots of RAM and even faster GPUs. Ubuntu-Gnome isn't far behind. None of the three are meant for "ancient hardware" because they impose too much strain on such systems trying to display their pretty effects such as "UI transparency".
[*]The really light flavours are Lubuntu and Ubuntu-Mate which still use 2-D desktops and don't run special effects. Xubuntu is only slightly heavier and many find it to be the ideal compromise between lightness and looks.
[*]While your description of the problem is quite complete, we really have no hard info on your actual system except subjective phrases like "ancient". Therefore, please post output of:```
sudo lshw -c system -c processor -c display -c memory -sanitize
``````
sudo lspci -vk | grep -iA15 vga
``````
glxinfo | grep "renderer string"
``````
xrandr
```
[/LIST]
Without knowing anything more about your system, I would strongly recommend that you avoid Ubuntu altogether and install one of the lighter flavours. You can try them out using a LiveUSB to see which one you prefer.

---

### Post by DuckHook on 2017-02-23
One further thought&#8230;

Yaketty (16.10) is not a good choice for a version. It only has four months of support left. All of the non-LTS releases are designed for people who have bleeding-edge HW or else power-users who tinker with kernels and drivers in their sleep. The most stable and well-supported versions come out every two years in April. The last one was Xenial (16.04) and is supported for three years in the lighter flavours. That is the one I would strongly encourage you to stick with. Otherwise, you are resigning yourself to the six-month new-install treadmill, which is just an ordeal, especially when running older equipment.

---

