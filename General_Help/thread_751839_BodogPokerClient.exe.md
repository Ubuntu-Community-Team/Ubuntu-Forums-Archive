---
title: "BodogPokerClient.exe    ???????"
date: 2008-04-10
forum: General Help
---

### Post by joecagle77 on 2008-04-10
Has anyone found a way to install this? I like bodog and dont want to go back to windows.

---

### Post by Rhubarb on 2008-04-10
Try running it under wine.
```
sudo aptitude install wine
```
Then run the program by double-clicking on the exe, or by placing the .exe in your home folder, then open up a terminal and type in:
```
wine BodogPokerClient.exe
```

Alternatively, you can run existing poker clients such as pokerth - get it by:
```
sudo aptitude install pokerth
```

---

### Post by joecagle77 on 2008-04-10
I did what you said with the wine BodogPokerClient.exe and everthing thing locks up. if I double click it I get "No application suitable for automatic installation is available for handling this kind of file"

I figured I may need to config wine but it then locks up

---

### Post by Rhubarb on 2008-04-11
After doing a quick search on the internet, it seems you need internet explorer 6 installed before your poker program can work.

Here's a link that can get you started:
[http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/](http://www.mattahfahtu.com/2007/02/20/howto-install-and-use-poker-clients-under-linux-with-wine/)
Please note that you already have wine installed, you just need to configure wine, and install IE6.

I can't help you much more than this.  As I have no interest in poker / installing bodogpoker.
Best of luck ;)

---

### Post by TheRingmaster on 2008-04-11
yeah that's a windows app. anything with .exe is. Either try using wine or don't use it at all (because you can't :)

---

### Post by atomkarinca on 2008-04-11
Instead of installing IE6, you can install [IEs4Linux]("http://www.tatanka.com.br/").

---

### Post by Tomatz on 2008-04-11
> **atomkarinca said:**
> Instead of installing IE6, you can install [IEs4Linux]("http://www.tatanka.com.br/").

Don't do this as ies4linux dosent install into your wine drive.

Basically it won't run with the poker app this way ;)

---

### Post by Tyke91 on 2008-04-11
have you tried downloading virtualbox and installing a windows virtual machine? that way you can run your windows specific apps without restarting

---

