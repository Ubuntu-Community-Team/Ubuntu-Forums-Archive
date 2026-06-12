---
title: "Removing Games"
date: 2006-12-12
forum: General Help
---

### Post by textguru on 2006-12-12
How can I remove all the games?

---

### Post by loell on 2006-12-12
i think you have to know each name of the game

then you can

```
sudo aptitude remove name_of_the_game
```

---

### Post by textguru on 2006-12-12
> **loell said:**
> i think you have to know each name of the game

then you can

```
sudo aptitude remove name_of_the_game
```
have tried it but I think package cannot be found.

have tried removing blackjack but system cannot find blackjack package.

---

### Post by v8YKxgHe on 2006-12-12
I thought the games that come with Gnome ( assuming your using Gnome ) are gnome-games?

```
sudo apt-get remove gnome-games
```

---

### Post by textguru on 2006-12-12
> **AlexC_ said:**
> I thought the games that come with Gnome ( assuming your using Gnome ) are gnome-games?

```
sudo apt-get remove gnome-games
```
Got what I needed! thanks! Case close.

---

