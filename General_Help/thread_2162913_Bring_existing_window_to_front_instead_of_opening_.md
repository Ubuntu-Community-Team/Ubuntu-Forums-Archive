---
title: "Bring existing window to front instead of opening a new one."
date: 2013-07-16
forum: General Help
---

### Post by Klainn on 2013-07-16
I searched around the forums but couldn't find anything that matched what I was actually looking for. If you know where the post it, please link me to it.

I've been using RedHat Linux at work for years and have decided to switch to Ubuntu. There's one function in fedora/redhat that I'm missing and am sure I can replicate in Ubuntu, I just don't know how. In RedHat, when I open a window (say chrome) for the first time and new window is opened, as expected. When I click on the chrome shortcut again, the open window is brought to the front, a new window is not opened. This is the same with the terminal and any other application. On my ubuntu install, every click of the shortcut opens a new window, regardless of the program.

How can I go about forcing the OS to use existing windows instead of opening new ones?

Thanks for reading!

---

### Post by 3rdalbum on 2013-07-16
If you are using Unity, I'm stumped - because the behaviour you want is exactly what Unity does, so no idea why it works differently for you.

Are you using the default desktop (Unity) or something different?

---

### Post by Klainn on 2013-07-16
Oh! I forgot to mention that. I am using Xfce.

---

### Post by stinkeye on 2013-07-16
The default xfce desktop shows an unexpanded bottom panel with launchers which as you found out
just launches apps.
You could remove the bottom panel and replace with Plank which is a very simple dock
with the functionality you want.
[**_[COLOR="#B22222"]Plank ppa[/COLOR]_**]("https://launchpad.net/~ricotz/+archive/docky")

```
sudo add-apt-repository ppa:ricotz/docky
sudo apt-get update
sudo apt-get install plank
```

Youtube-----> [**_[COLOR="#B22222"]Plank dock installation in Ubuntu XFCE[/COLOR]_**]("http://www.youtube.com/watch?v=3MnWksuLTb8")

---

### Post by Klainn on 2013-07-16
This is exactly what I was looking for.

Thanks much stinkeye!

---

