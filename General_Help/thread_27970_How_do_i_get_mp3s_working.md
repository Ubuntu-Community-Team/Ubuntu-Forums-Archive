---
title: "How do i get mp3s working?"
date: 2005-04-18
forum: General Help
---

### Post by Boopop on 2005-04-18
Hi,

Just installed my first ever linux yesterday, all this trying to install stuff is proving difficult  :???: . I've downloaded gstreamer 0.8 to try and play mp3s but i don't have a clue how to install it.Any help?

Also I was wondering how I can permanantly mount my windows hd so i can read files from it, currently i have to do it each time. Also can you reccomend a msn messenger clone and how I install it.

Thanks in advance, Boopop  ;-)

---

### Post by Bob D. on 2005-04-18
> Just installed my first ever linux yesterday, all this trying to install stuff is proving difficult ??: . I've downloaded gstreamer 0.8 to try and play mp3s but i don't have a clue how to install it.Any help?
I'd recommend you read the UbuntuGuide for Hoary @ [http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/) . Should answer most, if not all of your questions.

MP3 support: try the Ubuntu Wiki here - [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)

> Also I was wondering how I can permanently mount my windows hd so i can read files from it, currently i have to do it each time.

Permanent mounting of Windows NTFS partition, read only; [http://ubuntuguide.org/temp/#automountntfs](http://ubuntuguide.org/temp/#automountntfs)

> Also can you reccomend a msn messenger clone and how I install it.

Gaim, which is installed as part of a default Ubuntu install. See Applications>Internet>Gaim Internet Messenger from the drop down menu. I use it for MSN...had a long chat with my cousin in England this weekend. No webcam support built in however.

Bob

---

### Post by Boopop on 2005-04-18
I tried 'adding the extra repositories' and there was nothing there to replace, but i put it there anyway, and then it wudn't let me save it  :-? 

Help please  ](*,)

---

### Post by carlc on 2005-04-18
Assuming that you are following the guide, did you use the "sudo" command when you opened sources.list in gedit?


> sudo gedit /etc/apt/sources.list

---

### Post by wadageek on 2005-04-18
You need the gstreamer0.8-**mad** which is part of the Restricted section



> **Bob D.]I'd recommend you read the UbuntuGuide for Hoary @ [http://ubuntuguide.org/temp/](http://ubuntuguide.org/temp/) . Should answer most, if not all of your questions.

MP3 support: try the Ubuntu Wiki here - [http://www.ubuntulinux.org/wiki/RestrictedFormats](http://www.ubuntulinux.org/wiki/RestrictedFormats)



Permanent mounting of Windows NTFS partition, read only said:**
> http://ubuntuguide.org/temp/#automountntfs[/url]



Gaim, which is installed as part of a default Ubuntu install. See Applications>Internet>Gaim Internet Messenger from the drop down menu. I use it for MSN...had a long chat with my cousin in England this weekend. No webcam support built in however.

Bob

---

### Post by Boopop on 2005-04-18
Sorted it now, thanks for the help  :smile:

---

