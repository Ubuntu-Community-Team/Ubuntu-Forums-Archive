---
title: "Need help installing pSX playstation emulator"
date: 2007-04-13
forum: General Help
---

### Post by Coop on 2007-04-13
Hello

I am trying to install the pSX playstation emulator.

I am following [this]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_pSX_.28Playstation_Emulator.29") guide.

I am doing the manual way.

I have done upto this command: > sudo dpkg -x libgtkglext1_1.0.6-2.1ubuntu1_i386.deb libgtkglext

However, when I do this command: > sudo mv -v libgtkglext/usr/lib/* /usr/lib32/

it says: > :~$ sudo mv -v libgtkglext/usr/lib/* /usr/lib32/
mv: target `/usr/lib32/' is not a directory: No such file or directory


Please tell me what to do.

I will highly appreciate your help.

---

### Post by acormack on 2007-04-14
I don't use am64 but on my 32 bit Edgy system

/usr/lib32 is just a directory that contains my binary nvidia driver.

I suspect you just need to create the directory before running the mv command.

**sudo mkdir /usr/lib32**

mine has the permissions:

drwxr-xr-x 3 root root 4096 2007-04-07 18:31 /usr/lib32

which you could create with 

**sudo chmod 755 /usr/lib32**

Hope this helps

---

### Post by Coop on 2007-04-19
Thank you acormack.
I'll try your suggestion.

---

### Post by dfreer on 2007-07-01
Did you get pSX working coop?

---

