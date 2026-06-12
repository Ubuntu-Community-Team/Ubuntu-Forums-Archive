---
title: "sndfile issues: make install issue, undefined reference to `sf_open' issue"
date: 2015-01-24
forum: General Help
---

### Post by abc7 on 2015-01-24
sndfile - two issues: 1) make install or sudo make install The link here argue against the sudo comment, if I am not mistaken: [https://forums.opensuse.org/showthread.php/395758-mkdir-cannot-create-directory-permission-denied](https://forums.opensuse.org/showthread.php/395758-mkdir-cannot-create-directory-permission-denied)
  Anyway I was eager to compile and used sudo and it worked - question is could I have done it any better?


  2) ran gcc -lsndfile -o xxx xxx.c from src directory where sndfile.o exist - got multiple the errors like: undefined reference to `sf_open'
  Question is what is the fix... why it happened ... there are others who got it right?
  Someone used this (works for me too) but seems cumbersome: gcc sndfile-to-text.c pkg-config --cflags sndfile pkg-config --libs sndfile -o sndfile-to-text Linky - [http://ubuntuforums.org/showthread.php?t=1144187](http://ubuntuforums.org/showthread.php?t=1144187)



 Note: I did take care of: '/usr/local/lib/pkgconfig' to the PKG_CONFIG_PATH environment variable - hope I did it correctly: export PKG_CONFIG_PATH=/usr/local/lib/pkgconfig source /etc/environment echo $PKG_CONFIG_PATH
      

Pls help, thanks

---

### Post by coffeecat on 2015-01-25
Not a tutorial.

*Thread moved to **General Help**.*

What operating system/distro are you using?

---

