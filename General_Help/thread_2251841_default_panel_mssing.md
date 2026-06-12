---
title: "default panel mssing"
date: 2014-11-07
forum: General Help
---

### Post by sean69 on 2014-11-07
I don't know how I did it but I made the default panel disappear (lubuntu 14.10) I want it back
please step by step

---

### Post by Bucky Ball on 2014-11-07
Can you right click the desktop>application>log out>log out>log back in again. That should restart the panel. Unsure what panel Lubuntu uses, but you can also restart it from the terminal. Unsure of the command as don't use Lubuntu. ;)

---

### Post by Nairolf2112 on 2014-11-07
I had this problem recently ([http://ubuntuforums.org/showthread.php?t=2251190](http://ubuntuforums.org/showthread.php?t=2251190))
Thanks to this question in stack exchange, I've succeeded to fix it : [http://askubuntu.com/questions/64631/ho &#8230; untu-panel]("http://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel")

Here, what I've done to solve it : 
```
sudo cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
```

In askubuntu.com, they tell to do others commmands, but they didn't work with me. 
I don't have any problem now, so I think I've fixed it. 

Good luck ;)

---

### Post by sean69 on 2014-11-08
> **Nairolf2112 said:**
> I had this problem recently ([http://ubuntuforums.org/showthread.php?t=2251190](http://ubuntuforums.org/showthread.php?t=2251190))
Thanks to this question in stack exchange, I've succeeded to fix it : [http://askubuntu.com/questions/64631/ho … untu-panel]("http://askubuntu.com/questions/64631/how-to-restore-the-default-lubuntu-panel")

Here, what I've done to solve it : 
```
sudo cp /usr/share/lxpanel/profile/Lubuntu/panels/panel ~/.config/lxpanel/Lubuntu/panels
```

In askubuntu.com, they tell to do others commmands, but they didn't work with me. 
I don't have any problem now, so I think I've fixed it. 

Good luck ;)

thank you it's back those links helped

I'm now marking this thread closed

final solution was
```
 
sudo chown owner:group  ~/.config/lxpanel/Lubuntu/panels/panel
lxpanelctl restart 
```

---

