---
title: "Snap store doesn't load"
date: 2023-06-10
forum: General Help
---

### Post by fossfan2005 on 2023-06-10
Hi,

I recently installed 23.04 on my laptop. When I click on the Ubuntu Software icon, the app store does not load. This has been a problem since the installation. I thought running an APT upgrade would fix it but no luck so far. I subsequently installed Flatpaks and that is running fine. 

Thanks

---

### Post by Rubi1200 on 2023-06-11
Hi and welcome to the forums :-)

What error message do you get when trying to open the snap store?

This >> “Segmentation fault ( core dumped)” ?

What is your default system language?

---

### Post by papakanush2 on 2023-06-11
This happens frequently to me too. From searching the internet, I found the following fix:

```
sudo killall snap-store
sudo snap refresh snap-store
```

This solves the problem every time for me. 

For convenience (because it happens often enough) I just made this a shell script in my home directory to run whenever I need to.

---

