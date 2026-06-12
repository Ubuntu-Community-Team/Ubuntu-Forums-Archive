---
title: "ivtv nightmare"
date: 2005-05-21
forum: General Help
---

### Post by mahiman on 2005-05-21
i have a pvr150 and i just cant seem to get it to work.
i have been trying for the past 3 days with various errors and no success.

i am using 2.6.10-5-686-smp nothing special (p4). sources are installed
but i keep getting this error after i moved the files from /lib/modules/2.6.10 (dont know why it went there, something i did i am sure) to /lib/modules/2.6.10-5-686-smp/kernel/drivers/ivtv

depmod -a
extracted the beautiful firmware from the cd (and tried the zip file also)


but now i get this when i do an modprobe...

Error inserting ivtv (/lib/modules/2.6.10-5-686-smp/kernel/drivers/ivtv/ivtv.ko): Unknown symbol in module, or unknown parameter (see dmesg)


so i check dmesg | grep ivtv


ivtv: Unknown symbol video_device_release
ivtv: Unknown symbol video_unregister_device
ivtv: Unknown symbol video_device_alloc
ivtv: Unknown symbol video_register_device
ivtv: Unknown symbol video_usercopy
ivtv: Unknown symbol video_device_release
ivtv: Unknown symbol video_unregister_device
ivtv: Unknown symbol video_device_alloc
ivtv: Unknown symbol video_register_device
ivtv: Unknown symbol video_usercopy
ivtv: Unknown symbol video_device_release


just rerpeats...
at one point in time i did install them to /lib/modules/2.6.10-5-686-smp/kernel/drivers/media

and tried to run them..after trying driver .0.2 so i moved on to .0.3.5 and i wanted to remove them..i had a problem though. i simlinked an asterisk and couldnt remove it..so i tried to remove it. after hitting enter i remembered something called "regular expressions" (you may laugh). and removed every file (minus folders) from ../drivers/media

currently i am confused and fristrated (but still excited..'cause this is what it is about. this is how i learn right)...i gave up..and decided to throw in the towel and call for help...

if anyone knows what i should do, or you need any specific logs or messeges please.......help!!!

 :) 

sorry ofr any typos, i havent slept in a while....and took up smoking and coffee to get this right...

ps i am from freebsd land..so anything relative will help...
thanks a BUNCH!!

---

### Post by mahiman on 2005-05-22
no one has any similar experiences?

okay...well, thanks for your help.. ](*,)

---

