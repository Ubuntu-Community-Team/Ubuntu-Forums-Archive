---
title: "how to slow down &quot;all&quot; the compiz effects"
date: 2008-06-25
forum: General Help
---

### Post by dexter.deepak on 2008-06-25
i have tried it on gutsy, but dont remember how to slow down all the effects in hardy...mainly in order to take screenshots of intermediate states.

---

### Post by ruha on 2008-06-25
sudo apt-get install compizconfig-settings-manager.
You can adjust the settings for each effect here

---

### Post by dexter.deepak on 2008-06-25
i was actually asking for the key-bindings for slowing down "all" the effects in one shot ...and not individually

---

### Post by BlueSkyNIS on 2008-06-25
You will have to install compizconfig-settings-manager:

```
sudo apt-get install compizconfig-settings-manager
```


Under "General compiz options" put your favorite key-bindings, see screenshot.

---

### Post by sam1948 on 2008-06-25
if i remember correctly try
CTRL+s

---

### Post by dexter.deepak on 2008-06-25
i have tried everything..i had already enabled the "slow animations" in the general options and had made a key binding to <ctrl><super><alt>
..still the slowdown isnt noticeable at all !!
i have tried the keys repeatedly still it doesnt seem to work

---

### Post by Grishka on 2008-06-25
> **dexter.deepak said:**
> i have tried everything..i had already enabled the "slow animations" in the general options and had made a key binding to <ctrl><super><alt>
..still the slowdown isnt noticeable at all !!
i have tried the keys repeatedly still it doesnt seem to work

I don't think Ctrl+Super+Alt is a valid keybinding. try something like Super+F10, Ctrl+F7, Alt+Insert. or something like that.

---

### Post by dexter.deepak on 2008-06-25
thanks a lot Grishka ...that worked
but i feel its a bug in compiz..if i am trying an invalid key binding, i should have been given an error msg.

---

### Post by Grishka on 2008-06-25
> **dexter.deepak said:**
> thanks a lot Grishka ...that worked
but i feel its a bug in compiz..if i am trying an invalid key binding, i should have been given an error msg.

I don't think that's a problem with Compiz. there has always been a problem with modifier keys not registering when pressed together. they are not "proper" keys, you know, they are meant to do something only when some "normal" keys are pressed as well.

---

### Post by DaymItzJack on 2008-06-26
I'm pretty sure those are just extra keys to press, you need a key that isn't one of those three. If you did <Control><Alt><Shift>a or something, it would of probably worked.

---

### Post by mcurran on 2008-08-20
The default key combination (e.g. before you change it) is Shift+F10

Does anyone know how to make it so that the default is slow, so that you would press Shift+F10 to make it fast again, but have x start with them slow?

---

### Post by hellrealm on 2011-01-22
hey dude all u have to do to slow down ur animations is go into compiz-config settings manager then go to animations then from there choose an animation then select edit and you'll see duration it should be set at 80 by default if u want to make it just right setting it at 250 works perfect for me:p

---

### Post by mcurran on 2011-03-07
Thanks, but that does not answer my question.  I know how to make the animations slow, but I want a startup script that will have the slow animations already turned on.  Anyone know the compiz.real command for this feature/plugin?

---

