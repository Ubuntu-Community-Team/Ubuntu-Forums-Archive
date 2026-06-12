---
title: "Changing Permissions"
date: 2006-12-23
forum: General Help
---

### Post by Valinski on 2006-12-23
Hi im a bit new to linux and im having a some trouble changing the permission on my FlightGear directory. 

I typed the following.....

[COLOR="Blue"]dave@dave-desktop://usr/share/games$ sudo chmod FlightGear -w
[/COLOR]
and this changed the permission for all the folders within this folder but not the main directory. 
I need to be able to write to this directory as im trying to use terrasync. When i run the untility i get the following....

[COLOR="Blue"]receiving file list ... done
rsync: mkdir "/WorldScenery/Terrain/Terrain/w010n50/w003n54" failed: No such file or directory (2)
rsync error: error in file IO (code 11) at main.c(509) [receiver=2.6.8]
mkdir -p /WorldScenery/Terrain/Objects/w010n50
mkdir: cannot create directory `/WorldScenery': Permission denied
rsync --verbose --archive --delete --perms --owner --group scenery.flightgear.org::Scenery/Objects/w010n50/w003n54/ /WorldScenery/Terrain/Objects/w010n50/w003n54[/COLOR]

Any Help would be much appreciated. Thank you!:)

---

### Post by taurus on 2006-12-23
```
sudo chmod -R 777 FlightGear
```

---

### Post by Valinski on 2006-12-23
I just tried it but in the persmissions section it still says "Access Files" where as all the others inside the flightgear file say "create and delete files" . Any other ideas?

 Thank you for your time.

---

### Post by ruarymac on 2007-08-02
I had same problem.  It turns out that you don't have ownership of the directory.  This makes it hard to edit any files as you are not at 'root' in Ubuntu.  I used the 'chown' command on the FlightGear folder and changed the ownership to my user name.  Check the 'man' page on 'chown' to see how to use it.  Hope this helps.

Regards
Ruary

---

### Post by arbulus on 2007-08-02
try

```
sudo chown -R yourusername:yourgroupname /usr/share/games
```

that should change the ownership

then you can do

```
sudo chmod -R 777 /usr/share/games
```

hope this helps

---

