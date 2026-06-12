---
title: "Syncing a new cell phone/mp3 player"
date: 2007-12-04
forum: General Help
---

### Post by beejaycee on 2007-12-04
If this is in the wrong forum, a suggestion of a more appropriate one would be appreciated.

I have been slowly moving away from Windows to Ubuntu Gutsy and have been working to undue lots of whole habits.  I was fairly proud of myself when I finally stopped using iTunes to sync my iPod and learned how to use Amarok to download podcasts and sync them.  Now, I have a new cell phone, an SE w580i, and want to move away from using the iPod but I haven't been successful on how to sync the phone with Linux.  I am unable to use the phone to download the podcasts -- I don't know yet if this is a limitation of the phone or if AT&T has that blocked.  So far I have been manually saving the mp3s to the Linux desktop and copying them over to the phone's memory card.  Does anyone have any suggestions on an easier way to do this or can point me in the right direction?  I understand that I can buy a bluetooth dongle for the PCand do the file transfers but that still doesn't give me the ease of Amarok with my iPod, which is what I am working toward.

---

### Post by Claus7 on 2007-12-04
Hello,

maybe this will help :
[http://ubuntuforums.org/showthread.php?t=242932&highlight=multisync](http://ubuntuforums.org/showthread.php?t=242932&highlight=multisync)

Regards!

---

### Post by beejaycee on 2007-12-04
Thank you for the pointer to that thread but, unless I misunderstand what Multisync will do, this isn't quite what I'm looking for.  I don't really need to sync my address book/contacts/calendar with my phone.  

I'm trying to sync audio files to it the way I used to do with my iPod and Amarok (and iTunes before that).  Amarok would automatically download my podcasts and then I would click 2 or 3 buttons and they would transfer over to the iPod when it was connected.  I am not able to get Amarok to recognize the phone as an mp3 player so I have to manually download the files and move each over to the phone.

The link to the thread you gave me had several other links in it and I'll read through those and see if I can find any ideas.

---

### Post by beejaycee on 2007-12-06
Well, this turned out to simpler than it first appeared.  Amarok does everything I needed once I got it configured correctly.  Gutsy does not recognize the phone's memory but it does read the memory card.  I was pointing Amarok at "/sde1/..." instead of "/media/..." so once I corrected the mount point in Amarok, it's all good.

---

