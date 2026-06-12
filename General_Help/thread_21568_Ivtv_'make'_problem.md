---
title: "Ivtv 'make' problem"
date: 2005-03-22
forum: General Help
---

### Post by Klade on 2005-03-22
Hello

I'm running Hoary with all the upgrades etc. Recently I decided to turn my Ubuntu box into a Mythtv box. I popped in a pvr-150 and am now trying to get the darn thing to work. From what I understand I need ivtv to do this. 

I've looked around but no one seems to offer it in a way apt-get can download so that means just compiling it. This shouldn't be a big problem but for whatever reason it is. 

After I downloaded the file I decompressed it in /usr/src/ Then as per directions I opened up ivtv-0.3.2j/driver and ran 'sudo make' This however results in the following error:

make CONFIG_VIDEO_IVTV=m -C /lib/modules/2.6.10-5-686-smp/build M=/usr/src/ivtv-0.3.2j/driver modules
make: *** /lib/modules/2.6.10-5-686-smp/build: No such file or directory.  Stop.
make: *** [all] Error 2

After looking around online I found that this error results from me not having my kernel source code installed. So no biggy I downloaded 2.6.10 kernel source from synaptic and popped in the symbolic link in /usr/src directory to linux as per some instructions I found... well somewhere..

At any rate this has no effect at all on my error. So now I'm stuck. Anyone know what I need to do next?

P.S. I haven't had linux for all that long so if you know what I need to do please talk to me like I'm about 3 years old ;-)

---

### Post by Klade on 2005-03-23
Update: I did finally get the darn thing to compile. But not before accidentally deleting my nvidia kernel... Actually I'm not 100% sure how that happened but in the process of getting that reinstalled without X I was able to solve the above problem as well. I believe the issue revolved around me not having the correct version of the source. 

Now that it has at least compiled and installed I just need the rest of ivtv to work ;-) So while your reading this anyone happen to know where my Ivtv module went? When I modprobe ivtv it says it can't be found. I read someone elses notes on this board but they were using an older version and I don't seem to have the same directories they do. Also does anyone know if I need to download the firmware for my 150 card? Everyone seems to be talking about that for the 250 and 350 cards but haven't heard anything about the 150.

---

### Post by msmith on 2005-03-27
The issue with modprobe not finding ivtv after it'sbeen successfully compiled has to do with where make install puts the ivtv.ko, etc. files--see the post by cbozic here: [http://www.ubuntuforums.org/showthread.php?t=2878&highlight=ivtv](http://www.ubuntuforums.org/showthread.php?t=2878&highlight=ivtv)

Rather than copying the files as he did, though, I got it to work just by creating soft links to them. I did "find /lib/modules | grep ivtv" and saw they were in /lib/modules/2.6.10/ivtv/ , so I did:

ln -s /lib/modules/2.6.10/ivtv/* /lib/modules/2.6.10-5-386/kernel/drivers/media/video/

Then, "depmod" and "modprobe ivtv" worked fine.

---

