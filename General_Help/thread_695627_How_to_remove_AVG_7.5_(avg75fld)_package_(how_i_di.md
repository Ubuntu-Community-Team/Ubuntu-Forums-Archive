---
title: "How to remove AVG 7.5 (avg75fld) package (how i did anyway)"
date: 2008-02-13
forum: General Help
---

### Post by marshall.robert on 2008-02-13
After downloading the package of avg, either stopping the installation, or it failing avg my be a bit hard to remove.

How i did it was as follows:

create a dud avgd file:
```
sudo nano /etc/init.d/avgd
type something
ctrl+x (to exit)
y (to confirm changes)
```

then:
```
sudo update-rc.d avgd defaults
```

finally:
```
sudo apt-get remove avg75-fld
```

and thats how i removed avg :D hope this helps

---

### Post by K.Mandla on 2008-02-13
Moved to General Help.

---

### Post by Bluesluvr on 2008-04-18
THANKSSSSSSSS!!!!! This worked for me.

---

