---
title: "Send yes automatically"
date: 2017-04-03
forum: General Help
---

### Post by raleigh3 on 2017-04-03
Is there a way to send yes to this so it can run unattended ?

```
echo vvvv | sudo -S apt autoremove
```

---

### Post by bonestabone on 2017-04-03
yes

That's the command!

---

### Post by bonestabone on 2017-04-03
I'm not sure how you want to setup the script, but an example would be,

yes |  sudo -S apt autoremove

That will send the text 'y' as input to the apt command for as many times as needed.

---

### Post by deadflowr on 2017-04-03
```
sudo apt autoremove -y
```

---

### Post by raleigh3 on 2017-04-03
> **bonestabone said:**
> I'm not sure how you want to setup the script, but an example would be,

yes |  sudo -S apt autoremove

That will send the text 'y' as input to the apt command for as many times as needed.

Thanks, that's handy to know.

---

### Post by raleigh3 on 2017-04-03
> **deadflowr said:**
> ```
sudo apt autoremove -y
```

Thanks.

---

