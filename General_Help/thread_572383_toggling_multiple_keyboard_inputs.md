---
title: "toggling multiple keyboard inputs"
date: 2007-10-10
forum: General Help
---

### Post by mchnhed on 2007-10-10
Does anyone know how I can do the following:

1. toggle multiple keyboard inputs (more than 2)
2. have the panel indicator show the current keyboard
3. be able to switch keyboards quickly by pressing SHIFT+CTRL (as in Windows)

????

I have tried following the instructions on this website:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_keyboard_layouts_toggle_for_other_languages_.28Xfce.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_keyboard_layouts_toggle_for_other_languages_.28Xfce.29)


But here are my results:

```

username@computer:~$ setxkbmap -option grp:switch,grp:alt_shift_toggle,grp_led:scroll es,it,gr,us,jp,in
Error loading new keyboard description
username@computer:~$ 

```


I think it didn't work because I am trying to add more than 2 keyboard layouts. I tried it with two and it worked fine, however I am trying to be able to switch between 6 different ones. I also tried manually adding the keyboard layouts and the indicator to the panel by right-clicking on the panel and going to "Add to Panel..." but this didn't work either (It only allows a maximum of 4 keyboards, and when I do this it disables the quick-switch feature of pressing SHIFT+CTRL!)

AHHHHHHHHHHHHHHHHHHHHHHHHHH!!!!!!!!!!!!!!!!!!       :confused:

---

