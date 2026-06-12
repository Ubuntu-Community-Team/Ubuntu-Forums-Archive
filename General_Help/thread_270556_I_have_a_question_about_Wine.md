---
title: "I have a question about Wine"
date: 2006-10-03
forum: General Help
---

### Post by TheRingmaster on 2006-10-03
Is everything stored in the /.wine directory or do programs automatically store themselves else where.

I know that this is a misworded question but the bottomline is that I want to know where every file (that uses wine of course) is stored.

---

### Post by IcemanV9 on 2006-10-03
Yep, you are correct - it is stored in /.wine directory.

More info on Wine - [http://winehq.com](http://winehq.com)

---

### Post by TheRingmaster on 2006-10-03
I am having a small problem. what does this mean? see screenshot.

---

### Post by az on 2006-10-03
> **jpazindustries said:**
> I am having a small problem. what does this mean? see screenshot.

It means that wine cannot do something that the windows program needs it to do.

---

### Post by TheRingmaster on 2006-10-03
> **azz said:**
> It means that wine cannot do something that the windows program needs it to do.
but I am just opening the wine uninstaller??

---

### Post by IcemanV9 on 2006-10-06
Ha. Two things.

1) There is nothing to uninstall, so hence "nothing to do". If there are programs installed, then see wiki for more info on uninstall part.

2) Your Wine (0.9.9) is VERY old! You may want to update it to 0.9.22. Take a moment to read the ***[COLOR="Orange"][wiki]("https://help.ubuntu.com/community/Wine?highlight=%28wine%29")[/COLOR]*** on Wine.

---

### Post by alecjw on 2006-10-06
> **IcemanV9 said:**
> Your Wine (0.9.9) is VERY old! You may want to update it to 0.9.22.

And you can do so by typing in this in a terminal:
```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by TheRingmaster on 2006-10-07
thats the version that was in the repos

---

### Post by lemonsCC on 2006-10-07
I think there is another repo for "bleeding edge wine"

---

### Post by alecjw on 2006-10-07
> **lemonsCC said:**
> I think there is another repo for "bleeding edge wine"

Which you can get by adding this repository to you sources.list:
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
i don't think that there's an edgy one yet.

---

