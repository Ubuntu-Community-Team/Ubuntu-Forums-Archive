---
title: "Flash 9 beta and asound.conf"
date: 2006-10-30
forum: General Help
---

### Post by Greg T. on 2006-10-30
I had a [problem]("http://ubuntuforums.org/showthread.php?t=281695") getting sound to work with the Flash 9 beta but was able to overcome it this evening. Basically, sound was working in all applications except Flash 9. If you've had similar problems, check to see if you have an /etc/asound.conf file. If so, considering renaming it and rebooting (and subsequently deleting the file if Flash works). It did the trick for me; now Flash 9 works great. I've tried  many other applications and sound still works in them, too.

I had originally created the asound.conf file a long while ago following the advice in [this]("http://www.ubuntuforums.org/showthread.php?p=160497#post160497") HOWTO thread. However, more recent guidance in the thread indicates that the HOWTO is [URL="http://www.ubuntuforums.org/showpost.php?p=1419798&postcount=113
"]deprecated[/URL] and should not be followed.

The gist ***seems*** to be that the asound.conf file has been made unnecessary by other changes since the Hoary Hedgehog release (5.04), which is when I made the change. In my case, it could only make things worse, not better. Your mileage may vary, but again, it worked for me so I thought I'd relay my experience.

---

### Post by ltmon on 2006-10-30
Unfortunately the asound.conf file can be very important for users of certain sound cards.

Before Edgy came out, for example, I needed it to get a software volume mixer.... which for an unknown reason killed flash 9's sound.  Luckily for me the bug that required this has now been fixed - but I'm sure there's others in the same situation.

---

### Post by LO Matt on 2006-10-31
Thanks for the update.  I've kept an eye on your threads regarding this and tried the suggested fixes, as I also have a problem with Flash 9 sound.  Unfortunately, I do not have an asound.conf file, so this wont help me. :(  It looks like we had some of the same conditions, except I'm using Dapper (xubuntu).  Flash 7 worked fine for me, but this beta I can't get sound. I'm about ready to give up and go back to flash 7.  ](*,)  

M

---

### Post by Snowcat on 2006-11-02
After trying pretty much anything else suggested on the forums, this finally solved it for me! Thanks a lot! :-D 

I also have a system that I updated all the way from Hoary, and had an asound.conf file which I actually don't remember creating, but never mind! It works, and I'm happy :D 

Thanks again!

---

### Post by ~viper~ on 2006-11-11
Thank you!!!

---

### Post by raovq on 2006-11-20
this fixed my problem with sound in flash 9 in opera. yay!

---

