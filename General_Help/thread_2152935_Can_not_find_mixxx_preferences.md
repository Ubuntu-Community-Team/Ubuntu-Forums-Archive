---
title: "Can not find mixxx preferences"
date: 2013-06-09
forum: General Help
---

### Post by kahrkunne on 2013-06-09
Bit of a stupid question and probably the wrong place to ask it...
But I cant for the life of me find the preferences in Mixxx. How do I get to them?

---

### Post by Feathers McGraw on 2013-06-09
Hi,

At the top of the window there is a drop-down menu

options--> preferences should have what you're after.

If that's not what appears for you then you're probably running an old version (like the one that's included in the Ubuntu software centre), try adding the ppa to get the latest version (v 1.11.0).


To add the repository, enter these lines into the terminal:
```
sudo add-apt-repository ppa:mixxx/mixxx
sudo apt-get update
sudo apt-get install mixxx libportaudio2 
```

Note that the instructions on the mixxx website are incorrect, the first line appears as:

```
sudo add-apt-repository ppa:mixxx
```

...which doesn't work. Embarrassing really :p

Feathers

---

### Post by kahrkunne on 2013-06-09
Ah thank you. 
There is indeed no options drop-down menu.

I did try adding the ppa from the website but it said that it was unavailable and I thought I was my internet connection acting weird (again)

Hope this fixes it.


Still cant find this drop-down menu.

EDIT: It fails to assign the output when I start the application so it launches the preferences on startup...
This is a temporary workaround but I don really like relying on a bug to get things done.

---

### Post by Feathers McGraw on 2013-06-09
[IMG]http://i.imgur.com/agtHSel.png[/IMG]

Does your version not appear like this?

Try Ctrl+P

Feathers

---

