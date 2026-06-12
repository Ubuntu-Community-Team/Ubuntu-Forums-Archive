---
title: "problems with synaptic manager and updates"
date: 2006-12-22
forum: General Help
---

### Post by richardspirit on 2006-12-22
I posted this yesterday but have not found any resolutions. When I did the updates yesterday I got an undending loop with this error....

** (/usr/share/mono/MonoGetAssemblyName.exe:7945: CRITICAL **: _wapi_shm_semaphores_init: semget error: No space left on device. Try deleting some semaphores with ipcs and ipcrm

I checked my hard drive space and I am only using 9% of a 160gb drive, so that isn't the issue. Well today I another update notification and when I tried to update it said that I had to run 'dpkg --configure -a' manually to correct the problem...well I did that and I get the same loop and error as above...

---

### Post by richardspirit on 2006-12-22
I don't understand why nobody will help me...I have been respectful and posted as much information as possible...please help PLEASE!!!!

---

### Post by Mithrilhall on 2006-12-22
[http://www.google.com/search?q=_wapi_shm_semaphores_init%3A+semget+error&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=_wapi_shm_semaphores_init%3A+semget+error&ie=utf-8&oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by richardspirit on 2006-12-22
Thank you I will do some research and see if I can get it fixed...

One more question though....is there a way to uninstall these updates so that I can get the rest of my updates until I can get it fixed?

---

### Post by tommcd on 2006-12-22
Mithrilhall,
I tried googleing that error also. Were there any helpful links there that you found?
MonoGetAssemblyName.exe is listed as a DOS executable under properties for that file. I don't know what a DOS executable is doing on a linux system. I have that file also, but I do not get those errors. 
ipcs has something to do with interprocess communication. ipcrm will remove message  queues,  semaphore sets, or shared memory segments. Here are the man pages for those commands:
[http://www.linuxcommand.org/man_pages/ipcs8.html](http://www.linuxcommand.org/man_pages/ipcs8.html)
[http://www.linuxcommand.org/man_pages/ipcrm8.html](http://www.linuxcommand.org/man_pages/ipcrm8.html)
Just wanted to let you know I spent some time searching for a solution to this; and to subscibe to this thread. I never heard of this before. Googling was not very helpful.

---

### Post by Mithrilhall on 2006-12-22
I'm not sure what that means but it's worth a shot.


> He needs to run "ipcs -s" and delete the semaphores that look like
"0x4d036b25 156139526  dick      600        8" (the fingerprint numbers
are the 600 perms and 8 nsems) with ipcrm. 

The DOS executable is from the Mono project it looks like. Did you try to install Mono at one time?

---

### Post by tommcd on 2006-12-22
Hmmm, I don't have Mono, but I have one of it's dependencies for some reason: libmono-corlib1.0-cil. What else would that dependency be for?

---

### Post by richardspirit on 2006-12-22
> **Mithrilhall said:**
> I'm not sure what that means but it's worth a shot.




The DOS executable is from the Mono project it looks like. Did you try to install Mono at one time?

Okay I found what he what I need to delete by running the command but I don't know the command to actually delete it...

I don't if I have installed Mono or not...it doesn't sound familar but I install programs all the time to see how they work and if I can get them to work....

---

### Post by richardspirit on 2006-12-22
*bump

---

### Post by richardspirit on 2006-12-24
I fix this problem by running apt-get remove dash then I was prompted to run dpkg --configure -a again( the last time I ran the dpkg command it went into the infinite loop ) this time everything worked!!!!

---

### Post by tommcd on 2006-12-24
Richard,
How did you know that you needed to remove Dash? Did you run icps and icprm?  You can check if Mono is installed by searching for it in synaptic.
Glad you got it fixed.

---

