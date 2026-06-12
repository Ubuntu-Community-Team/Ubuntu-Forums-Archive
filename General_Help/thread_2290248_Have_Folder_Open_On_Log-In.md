---
title: "Have Folder Open On Log-In"
date: 2015-08-10
forum: General Help
---

### Post by Zim_Zim_Zalabim on 2015-08-10
I have found how to have an application start when you log-in, but how do you set a folder to open when you log in?

---

### Post by tgalati4 on 2015-08-10
Welcome to the forums. You can add the following to your startup application list:

```
nautilus /home/zim_zim/the_folder_you_want_to_open
```

---

### Post by Zim_Zim_Zalabim on 2015-08-11
If I type in terminal the below command it returns telling me the folder doesnt exist
```

nautilus /home/Downloads

```

---

### Post by mc4man on 2015-08-11
that would be nautilus /home/[COLOR="#FF0000"]username[/COLOR]/Downloads where the red has your username
Though for this purpose this would suffice
```
nautilus Downloads
```

---

### Post by mc4man on 2015-08-11
If you have any issue with this I'd add a small delay to the autostart .desktop (located in ~/.config/autostart), 1 or 2 sec.'s would be about right.
just add this line to the .desktop
```
X-GNOME-Autostart-Delay=1
```

(I'd likely not use Startup Applications to create the final startup app (.desktop),  as it creates command.desktop so in this case nautilus.desktop. May be better to have it named something else like nautilus1.desktop, note though that a .desktop can not be renamed, it is named at creation.. only

---

