---
title: "android application cannot connect to ubuntu server!"
date: 2015-03-11
forum: General Help
---

### Post by jayon on 2015-03-11
I have made a android application(Eclipse windows) that connects to ubuntu server runnin in oracle virtual box.
I provided the IP address...but the connection gets failed!
please refer to the attachment--->the code of android app and the ubuntu server cmd images!

---

### Post by nerdtron on 2015-03-11
is apache running on the virtual machine?

```
sudo service apache2 start
```

---

### Post by jayon on 2015-03-11
yes it shows.... already runnin :(

---

### Post by jayon on 2015-03-11
did i used the IP address in the correct form???

---

### Post by nerdtron on 2015-03-11
from your windows 7 host, open a web browser and see it you can access the url [http://192.168.56.102/register.php](http://192.168.56.102/register.php)

---

