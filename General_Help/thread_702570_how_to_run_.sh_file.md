---
title: "how to run .sh file"
date: 2008-02-20
forum: General Help
---

### Post by chayanvinayak on 2008-02-20
Hi ,

I am using Ubuntu 7.0.1 , I am trying to run a .sh file.
( this .sh file is to run a software named "shake" ).


When I have "run as script" on for that file and i double click the file nothing happen.
when I have "run as script" off , it opens the file as text.

Kindly suggest


Thanks

---

### Post by jken146 on 2008-02-20
Assume the script is called myScript.sh and is in your home directory.

Open up a terminal (Applications -> Accessories -> Terminal) and type 
```
chmod o+x myScript.sh
```
then
```
./myScript.sh
```

---

### Post by wirelessmonkey on 2008-02-20
FYI, Apple doesn't support shake on anything other than ubunu 6.06LTS, and install instructions are included with legitimate copies.

---

### Post by chayanvinayak on 2008-02-20
thanks jken, 

Are u sure, it will work , because i had 777 permission on that file.
And to check your technique i will have to reinstall Ubuntu :) .

thanks alot though.

---

### Post by chayanvinayak on 2008-02-20
hi wirelessmonkey,

As 6.0.1 Lts is not available on Ubuntu.com , 
Will Shake work on 6.0.6 LTS ?

Thanks

---

### Post by wirelessmonkey on 2008-02-20
chayanvinayak,

Sorry, that was a typo on my part.  Didn't your copy come with install instructions?   .........  If not, you should contact your vendor.

---

### Post by ruy_lopez on 2008-02-20
> **jken146 said:**
> Assume the script is called myScript.sh and is in your home directory.

Open up a terminal (Applications -> Accessories -> Terminal) and type 
```
chmod o+x myScript.sh
```
then
```
./myScript.sh
```

chmod o+x makes it executable to 'others'. It should be 'chmod u+x' if you are being selective (u is the file owner permission). Otherwise 'chmod +x' does the trick.

---

