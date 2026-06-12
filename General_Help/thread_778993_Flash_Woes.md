---
title: "Flash Woes?"
date: 2008-05-02
forum: General Help
---

### Post by karuptdata on 2008-05-02
Hello all,

I recently switched back to Ubuntu in anticipation of 8.x release. I have to admit i am very impressed. However i am experiencing one issue that is driving me insane. Hopefully you guys will be able to shed some light on this one for me. 

Whenever i navigate via any browser to a page that includes flash i get a gray box with a play symbol instead of the actual flash rendering. Adobe is installed however i still have the same issue. I have included a screenshot so i can show you what i am seeing. Any help is greatly appreciated.

Regards,

Karuptdata

---

### Post by TeoBigusGeekus on 2008-05-02
Have you installed ubuntu-restricted-extras?

---

### Post by karuptdata on 2008-05-02
Yes ubuntu-restricted-extras is installed on the machine..should i remove this package?

---

### Post by albymilan on 2008-05-02
> **karuptdata said:**
> Hello all,

I recently switched back to Ubuntu in anticipation of 8.x release. I have to admit i am very impressed. However i am experiencing one issue that is driving me insane. Hopefully you guys will be able to shed some light on this one for me. 

Whenever i navigate via any browser to a page that includes flash i get a gray box with a play symbol instead of the actual flash rendering. Adobe is installed however i still have the same issue. I have included a screenshot so i can show you what i am seeing. Any help is greatly appreciated.

Regards,

Karuptdata

Hi, i also had this problem. Try to do this:
-uninstall the flash plugin you have first time installed
-go to a website with something in flash
-firefox must show you that you need a plugin. click on that advice
-install the SECOND choice (adobe flash installer or something like this)

Enjoy ;)

---

### Post by TeoBigusGeekus on 2008-05-02
Definitely not! That's the package that contains the flash plugin, mp3 codecs, extra fonts, etc.
Have you tried Opera to see if flash is working in it? 
I say this cause I read numerous posts about problems with Firefox in Hardy. If you are using the FF3 beta, you could also downgrade to FF2.
But I strongly recommend Opera 9.50b2: more stable than ever, not a resource hog like Firefox and (at least in my system) flash works. 

(TO THE OPERA GUYS: I'M WAITING FOR THAT CHEQUE :lolflag: )

---

### Post by karuptdata on 2008-05-02
LOL Thanks alot for the info guys, odly enough this happens in any browser that i install. I have the following installed on the pc: Firefox, Opera, SeaMonkey. Im beginning to wonder if the flash plugin i installed is having some issues. Can someone tell me where to remove the flash plugin. Im a bit rusty its been a while since i ran Ubuntu as my primary...

---

### Post by TeoBigusGeekus on 2008-05-02
Go to synaptic and do a search for flash.

---

### Post by karuptdata on 2008-05-02
Ok i seemed to have resolved my problems for now, I launched synaptic and removed all flash related entries that i had. Reinstalled flash manually and viola all set to go. Thanks for helping out here guys :)

---

### Post by robertchahine on 2008-05-02
congratulations. beacause i had the same issue, but i can't uninstall the flash plugin from synaptic beacuase of this error
 [http://ubuntuforums.org/showthread.php?p=4863477#post4863477](http://ubuntuforums.org/showthread.php?p=4863477#post4863477)

---

