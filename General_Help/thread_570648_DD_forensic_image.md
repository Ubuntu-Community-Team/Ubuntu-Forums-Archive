---
title: "DD forensic image"
date: 2007-10-08
forum: General Help
---

### Post by FrankoNL on 2007-10-08
Hello everyone!:)

i'm new with Ubuntu, i need it for my education ( digital forensic investigator) and now i need to make forensic copy's in windows and in ubuntu with the DD command, and after that i have to compare the MD5 hash value between the original and image. can you guys direct me to a nice website where i can learn more about how i need to use the command etc? it would really help me out a lot.

---

### Post by defishguy on 2007-10-08
This should be a good start for you:

[http://www.debianhelp.co.uk/ddcommand.htm]("http://www.debianhelp.co.uk/ddcommand.htm")

Good luck!

---

### Post by Linder on 2008-02-28
This is like....necro deluxe, but check out Helix at [http://www.e-fense.com/helix/](http://www.e-fense.com/helix/)

---

### Post by trobbins on 2008-02-28
This is by far my favorite dd example forum posting that I have seen:

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/)

It covers many uses for dd.

To keep it simple, here is how I would image a drive:

dd if=/dev/hda of=/home/trobbins/myimage.ima bs=4096

I would then run 

md5sum /dev/hda

and then:

md5sum /home/trobbins/myimage.ima

---

