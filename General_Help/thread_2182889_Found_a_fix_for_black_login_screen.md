---
title: "Found a fix for black login screen"
date: 2013-10-22
forum: General Help
---

### Post by Matt12334 on 2013-10-22
Not sure if this is in the right place, but I'm sure this will help at least somebody...

Edit /etc/init/lightdm.conf 

Right before the  following line:
```
    exec lightdm
end script
```

add this:

```
sleep .5
```

... so it should look like:

```
    sleep .5
    exec lightdm
end script
```

This prevents your computer from jumping the gun and trying to start lightdm before it's ready to do so. Let me know if this helps!

---

