---
title: "Re: mail-notification : no sound"
date: 2015-12-30
forum: General Help
---

### Post by marsdenf on 2015-12-30
Using xubuntu 14.04.  I bought a pair of polk hampden speakers. I  had a bit of a struggle to get them to work with the digital connection  (usb) but now it seems that all sound programs work, except for  mail-notification. (The analog connection never worked for these new  speakers, and I didn't want it anyway.)  The program works properly  except the sound notifier doesn't play any file. (It worked with my  older analog speakers.) 

   When mail-notification properties is opened, and I try to test play  a wav file in the selection window, no sound is heard.  But the "stop"  button becomes unshaded for a fraction of a second and then becomes  shaded out again.  I tried playing a much longer sound file and the same  thing happened.  It seems like the program starts to play the file and  then something immediately crashes.  In configuration editor, the  generic command for mail-notification to play a sound file is: 

 exec gst-launch-0.10 filesrc location=%file ! decodebin ! audioconvert  ! gconfaudiosink >/dev/null 2>&1 


   I opened a terminal and put the command in, with " file " replaced  by an actual file location, as follows: 

exec gst-launch-0.10 filesrc location=%/home/marsdenf/Music/Notification  Sounds/dogbarkMuchLouder.wav ! decodebin ! audioconvert ! gconfaudiosink  >/dev/null 2>&1 


   After pressing enter in the terminal, the terminal immediately  closed out (crashed) and no sound was heard. 

Any suggestions?

I realized my mistake in including the " % " character with the  command, and tried it without it, and the same thing happened.  I also  tried renaming the file " Notification Sounds " to " NotificationSounds  " to eliminate the white space, but the same thing happened.  (The  whitespace had not been a problem before the new speakers.)

---

### Post by raonyguimaraes on 2016-02-23
I have exactly the same problem ... have no idea what is causing this ... I see you reported a bug 

[https://bugs.launchpad.net/mail-notification/+bug/1530215](https://bugs.launchpad.net/mail-notification/+bug/1530215)

---

