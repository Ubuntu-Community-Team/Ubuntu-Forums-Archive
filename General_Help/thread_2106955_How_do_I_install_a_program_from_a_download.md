---
title: "How do I install a program from a download?"
date: 2013-01-20
forum: General Help
---

### Post by DivingHawk on 2013-01-20
This may sound silly but here goes. I'm trying to download Supertuxkart 0.8 from the website but every time I try it keeps opening archive manager. How do I get the files on supertuxkart to the point where I can search for it on my desktop, click, and play.

---

### Post by COMECON on 2013-01-20
I recommend you to install Supertuxkart through the backports repositories.

**Ubuntu 12.04 Precise Pangolin**:
```
sudo apt-get install -t precise-backports supertuxkart 
```**Ubuntu 12.10 Quantal Quetzal**:
```
sudo apt-get install -t quantal-backports supertuxkart
```And that should install you Supertuxkart!

esy

---

### Post by DivingHawk on 2013-01-20
Do I still have to download it from the site first?

---

### Post by circa on 2013-01-20
Supertuxkart is located in the Ubuntu Software Center. Look under Games -> Simulation. This would make it much easier for you to install. No need to mess with tar balls.

---

### Post by DivingHawk on 2013-01-20
Only problem with that is when I tried to download it from the software center it gave me 0.7 which has a few glitches.

---

### Post by DivingHawk on 2013-01-20
This didn't work.

E: The value 'quantal-backports' is invalid for APT::Default-Release as such a release is not available in the sources

---

### Post by circa on 2013-01-20
I got ya. Go back to their website...

[http://supertuxkart.sourceforge.net/Build_STK_on_Linux](http://supertuxkart.sourceforge.net/Build_STK_on_Linux)

They give you detailed build instructions.

---

### Post by DivingHawk on 2013-01-20
Thanks. Now what is the STK root source directory? I'm a little confused by step two.

---

### Post by circa on 2013-01-20
The STK (SuperTuxKart) root directory is the folder's location in which you extracted the tar.gz file. This folder is where you'll build the file from.

---

### Post by DivingHawk on 2013-01-20
Sorry total newb here. And I already extracted the file using the terminal right? How do I find the folder?

---

### Post by circa on 2013-01-20
Probably not, unless you explicitly typed tar -zxvf (filename here).tar.gz. Locate your dowloaded tar file. Create a folder (on your desktop or somewhere you can easily locate) called stk (or any other name you wish). Double click the tar.gz file to open it, then right click and select "extract" and select the created folder to extract into. Now you should go into terminal and build the file from within the folder you created. (e.g. yourname@ubuntu:~/Desktop/stk$).

---

### Post by Cheesemill on 2013-01-20
No need to try compiling it yourself, just installing the .deb file for version 0.8 should work...

[32-bit]("http://mirror.leaseweb.com/ubuntu//pool/universe/s/supertuxkart/supertuxkart_0.8-1_i386.deb")
[64-bit]("http://mirror.leaseweb.com/ubuntu//pool/universe/s/supertuxkart/supertuxkart_0.8-1_amd64.deb")

---

### Post by DivingHawk on 2013-01-20
> **circa said:**
> Probably not, unless you explicitly typed tar -zxvf (filename here).tar.gz. Locate your dowloaded tar file. Create a folder (on your desktop or somewhere you can easily locate) called stk (or any other name you wish). Double click the tar.gz file to open it, then right click and select "extract" and select the created folder to extract into. Now you should go into terminal and build the file from within the folder you created. (e.g. yourname@ubuntu:~/Desktop/stk$).
Well I have it where I can run it now but it's in the folder (I extracted the contents of the folder using archive manager). It's a pain to run but it works.

---

### Post by DivingHawk on 2013-01-20
> **Cheesemill said:**
> No need to try compiling it yourself, just installing the .deb file for version 0.8 should work...

[32-bit]("http://mirror.leaseweb.com/ubuntu//pool/universe/s/supertuxkart/supertuxkart_0.8-1_i386.deb")
[64-bit]("http://mirror.leaseweb.com/ubuntu//pool/universe/s/supertuxkart/supertuxkart_0.8-1_amd64.deb")
Well I know how to download it but I have no idea how to install it.

---

### Post by Cheesemill on 2013-01-20
Those are the .deb files I linked to, they should just open automatically with the Software Centre and install.

Or you can just download it to your home folder then run..
```
sudo dpkg -i ~/supertuxkart_0.8-1_i386.deb
```

---

