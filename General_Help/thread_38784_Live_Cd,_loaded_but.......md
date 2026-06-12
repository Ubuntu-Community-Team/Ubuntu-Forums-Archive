---
title: "Live Cd, loaded but......"
date: 2005-06-02
forum: General Help
---

### Post by canada on 2005-06-02
After "root:" (could of been "user") came up i couldn't use my keyboard, nothing.

Any ideas?

---

### Post by canada on 2005-06-02
Seems the whole file didn't download. Does anyone else have problems downloading ISO's? I had the same problem with slax. Could it be that i'm using firefox? Every ISO i downloaded now never left my download box and i had to drag it from my temp files to my desktop to burn the ISO and it was successful once.

Preplexed in Canada.

---

### Post by tread on 2005-06-02
Try using wget to download the file .. also, before you burn the image, use md5sum to verify if you got the correct file and that its complete.

---

### Post by canada on 2005-06-02
Downloaded wget and tried to run it but the console? (black box) just pops up and disappears.

---

### Post by tread on 2005-06-02
it has to be run in a terminal. You need to get the url of the iso image (rightclick link in firefox and click copy link address)

then in the terminal type:
wget link_address. 

If the connection breaks, wget can resume downloads .. wget --help to check the parameter (I've forgotten)

---

### Post by canada on 2005-06-02
Maybe you didn't hear me; the terminal won't load, just kiddin :)  I will just try the plain download using FF.

thx

---

### Post by tread on 2005-06-02
ok :) I thought you were trying to doubleclick wget .. 
Firefox should suffice really, but remember to do an md5sum before you burn the image.

---

