---
title: "ICE authority"
date: 2013-01-12
forum: General Help
---

### Post by jeannotlapin36 on 2013-01-12
I'm french and i don't speak english fluently 
  I need ubuntu 10.04 - I'have reisntalled this 10.04 and now i 've a bug 
  my home is encoded : i don't know why 
  on ubuntu.fr a person says me this commands :
 
rm ./.ICEauthority && rm ./.Xauthority

do you now that ? 

thanks

or that 
rm ~/.Xautority
.or
mv ~/.Xautority ~/.Xautority-old


mv ~/.Xautority-old ~/.Xautority

---

### Post by oldfred on 2013-01-12
Welcome to the forums.

I do not know if deleting it will let it create a new one with correct ownership & permissions or not.

       .dmrc errors- drs305
[http://ubuntuforums.org/showthread.php?p=6161267](http://ubuntuforums.org/showthread.php?p=6161267)
.ICEauthority errors
[http://ubuntuforums.org/showthread.php?t=1590835](http://ubuntuforums.org/showthread.php?t=1590835)
chmod 755 /home/username
sudo chown $USER:$USER /home/username/.ICEauthority
sudo chmod 644 /home/username/.ICEauthority
sudo chmod 644 $HOME/.ICEauthority
look at the permissions on ~/.Xauthority, too. It often gets changed when ~/.ICEauthority gets changed. The same fix applies.

---

