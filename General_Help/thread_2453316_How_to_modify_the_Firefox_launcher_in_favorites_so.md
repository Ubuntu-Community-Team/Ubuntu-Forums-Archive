---
title: "How to modify the Firefox launcher in favorites so that it launches within a Firejail"
date: 2020-11-07
forum: General Help
---

### Post by linuxyogi on 2020-11-07
How to modify the Firefox launcher in favorites so that it launches within a Firejail sandbox ?

---

### Post by ajgreeny on 2020-11-07
You need to go to /usr/share/applications/firefox.desktop and open it in a text editor as root, eg ```
sudo nano /usr/share/applications/firefox.desktop
```
Look for the line ***Exec=firefox %u*** and change it to ***Exec=firejail firefox %u*** or whatever the command is to get firejail to work, (I haven't used it for years).

After editing save the new version as firejail-firefox.desktop and it will appear in your system's menus, whatever they are in the DE of your choice.
You may need to either logout or reboot for the new menu item to show.

---

### Post by Holger_Gehrke on 2020-11-07
Wouldn't it be easier to just copy the firefox.desktop from /usr/share/applications/ to $HOME/.local/applications/ and edit the copy ? No need for 'sudo' and this allows for configuration on a per user basis. Unless the point is to have two separate menu entries, in which case changing the line beginning with 'Name=' to reflect which starter is which would be a good idea.

Holger

---

### Post by linuxyogi on 2020-11-08
I did it like this

```
 cp /usr/share/applications/firefox.desktop /home/mrubuntu/Desktop/ 
```

Then I opened the launcher in gedit (as regular user) & added "firejail" to the exec line.

---

### Post by ActionParsnip on 2020-11-08
Note you can use "~" as a shortcut, so
```
 
/home/mrubuntu/Desktop 

``` 
Becomes
```
 
~/Desktop

```

---

### Post by ajgreeny on 2020-11-08
I assumed, perhaps wrongly that linuxyogi wanted Firefox  to always start using firejail.

Anyway, if looks as if this is now solved, and if so please  mark SOLVED from the Thread Tools menu up top.

---

