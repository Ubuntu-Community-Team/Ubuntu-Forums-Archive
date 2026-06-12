---
title: "Minbar"
date: 2007-04-08
forum: General Help
---

### Post by embeemb on 2007-04-08
I was trying to install itools for prayer times announcement and such, and someone suggested to get minbar instead.
I got the .deb package from [here]("http://http.us.debian.org/debian/pool/main/m/minbar/minbar_0.1-6_i386.deb") 

I downloaded the .deb package as told, however upon installation, I got an error message "Dependencies not satisfied: libatk1.0-0". 

I tried to >  sudo apt-get install libatk1.0-0 and the response confirmed I have the latest version. I also tried to change the permissions for the .deb package to allow it to be executed by owner, but I continue to get the same error message.

Any ideas?

---

### Post by ihavenoname on 2007-04-08
> **embeemb said:**
> I was trying to install itools for prayer times announcement and such, and someone suggested to get minbar instead.
I got the .deb package from [here]("http://http.us.debian.org/debian/pool/main/m/minbar/minbar_0.1-6_i386.deb") 

I downloaded the .deb package as told, however upon installation, I got an error message "Dependencies not satisfied: libatk1.0-0". 

I tried to  and the response confirmed I have the latest version. I also tried to change the permissions for the .deb package to allow it to be executed by owner, but I continue to get the same error message.

Any ideas?

Try installing 
libatk1.0-data 

sudo apt-get install libatk1.0-data  libatk1.0


Also, you could use this wiki page here [http://www.ubuntume.com/wiki/installation](http://www.ubuntume.com/wiki/installation)
and then this one. 
[http://www.ubuntume.com/wiki/islamiccal](http://www.ubuntume.com/wiki/islamiccal)
This is for an islamic calender. If that was all that you needed. Minbar also has prayer times. Once you check that libatk1.0-data I can help you more with that.

---

### Post by ihavenoname on 2007-04-14
I am very sorry, I the debian package I linked you to earlier DOES NOT work with Ubuntu. Here I have made one which *should*. Please tell me if it works.

Edit: sorry the deb is too large to attach (1.2 mb). If you want you can private message me your email address and I will email it to you.

---

