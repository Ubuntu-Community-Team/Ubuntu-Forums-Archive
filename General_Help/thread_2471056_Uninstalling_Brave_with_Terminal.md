---
title: "Uninstalling Brave with Terminal?"
date: 2022-01-20
forum: General Help
---

### Post by Daveski17 on 2022-01-20
Hello,

I’m not planning on uninstalling Brave any time yet. I just wondered what the Terminal commands were for uninstalling it completely. I’ve heard it isn’t so easy to uninstall. 

I installed it with [these commands]("https://brave.com/linux/#linux") on Ubuntu 20.04 LTS.

Thanks.

---

### Post by jimmy-frydkaer on 2022-01-20
> sudo apt purge brave
 
You can apt remove brave first but the result is the same

---

### Post by deadflowr on 2022-01-20
>  I&#8217;ve heard it isn&#8217;t so easy to uninstall.
Not sure how hard t can be to run apt purge brave.

Then you can just delete the source list file. ```
sudo rm /etc/apt/sources.list.d/brave-browser-release.list
```
Or if you gave it another name use that.
After that removing the apt-key is up to you as that is more or less just dead weight and useless. But also harmless.

Final action would be to purge the brave folders from your home folder.
Should have two folders, one inside the .config folder and the other inside the .cache folder.
See: [https://askubuntu.com/questions/1217043/how-do-i-remove-brave-completely]("https://askubuntu.com/questions/1217043/how-do-i-remove-brave-completely")


Note that only the first action is really needed to remove brave.
The actions of deleting the source list will simply make it easier on apt updating, since it will stop apt from trying to connect to a server that it no longer needs to connect to.
The last action of deleting the brave folders in your personal home folder is simply why keep 'em if you aren't going to use them.

---

### Post by Daveski17 on 2022-01-20
> **jimmy-frydkaer said:**
> You can apt remove brave first but the result is the same

OK thanks.

---

### Post by Daveski17 on 2022-01-20
> **deadflowr said:**
> Not sure how hard t can be to run apt purge brave.

Then you can just delete the source list file. ```
sudo rm /etc/apt/sources.list.d/brave-browser-release.list
```
Or if you gave it another name use that.
After that removing the apt-key is up to you as that is more or less just dead weight and useless. But also harmless.

Final action would be to purge the brave folders from your home folder.
Should have two folders, one inside the .config folder and the other inside the .cache folder.
See: [https://askubuntu.com/questions/1217043/how-do-i-remove-brave-completely]("https://askubuntu.com/questions/1217043/how-do-i-remove-brave-completely")


Note that only the first action is really needed to remove brave.
The actions of deleting the source list will simply make it easier on apt updating, since it will stop apt from trying to connect to a server that it no longer needs to connect to.
The last action of deleting the brave folders in your personal home folder is simply why keep 'em if you aren't going to use them.

Thanks. So sudo apt purge brave would basically do the job?

---

