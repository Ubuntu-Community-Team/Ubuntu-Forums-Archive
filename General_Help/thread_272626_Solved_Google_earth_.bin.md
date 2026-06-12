---
title: "Solved: Google earth .bin"
date: 2006-10-06
forum: General Help
---

### Post by alecjw on 2006-10-06
I've just downloaded google earth for Linux. It came as a .bin file but I don't know how to open it. Any ideas?

Edit: fixed it. I had to execute it in the terminal.

---

### Post by Ciego on 2006-10-06
You need to make the file executable before you can run it.

```
sudo chmod 755 /filelocation
```

Then you should be able to double click on the file and it will run.  Keep in mind you may have to execute the file as sudo.

---

### Post by wkulecz on 2006-10-06
I had to do it as root (sudo sh googleearth.bin) and as my normal user.  It worked after the root install but I couldn't create a menu entry for it until after I installed it again as my default login.

Not sure what's the cause here but its a cool program even though most of the images seem photos seem a couple of years old.

--wally.

---

