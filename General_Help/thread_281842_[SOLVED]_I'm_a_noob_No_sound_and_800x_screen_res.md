---
title: "[SOLVED] I'm a noob: No sound and 800x screen res"
date: 2006-10-21
forum: General Help
---

### Post by Kristopher on 2006-10-21
Hi all

I am new to Ubuntu so I hope you don’t mindme asking a few questions.

I am running Windows XP pro with Ubuntu as a VM (thought would do this to see what its like)

I downloaded 5.10 and it loaded ok everything was fine and I did an upgrade to 6.06  using the built in update system and my display went weird with blue and black horizontal lines and it didn’t even load. 

So I then downloaded 6.06 and booted it up in VMplayer and it has loaded with a 800 screen resolution which I can only change to 600 or 800 would like 1024 or higher and also no audio.

I have done a little reading and typed the lspci command and I cant see my soundcard there.

I have the following

Creative Sound Blaster Audigy and NVIDIA FX2000 graphics card.

Any help would be great

Thanks 
Kristopher

---

### Post by raul_ on 2006-10-21
I think that sound card is supported by alsa. try install the alsa-drivers. That should take care of the sound. As for the monitor, just search on the forums, i think it has been fixed.

---

### Post by Kristopher on 2006-10-21
Can you tell me how i install alsa (sorry just got into Ubuntu yesterday and dont know much)

Thanks

---

### Post by raul_ on 2006-10-21
[http://wingware.com/support/asus_z63a_ubuntu_5.10]("http://wingware.com/support/asus_z63a_ubuntu_5.10")

check out this link. I think it addresses your other problem too

---

### Post by Kristopher on 2006-10-21
Thanks I will take a look but I am still very confused at how to install things like this.

---

### Post by raul_ on 2006-10-21
Lol. It's very easy. Just open the synaptic packet manager (From System->Administration) and voila! there u have it. Anyway, check this out.
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

I think you'll be very comfortable having this in your bookmarks :D

---

### Post by Kristopher on 2006-10-22
Me again sorry about this, as i said am new to Ubuntu as i have been a windows user since Win95. I just started using Ubuntu as a VM Friday night.

Ok so i opened up the SPM and did a search for 915resolution but in the top right box was blank :-k 

I did the same for alsa and the boxes were green for 

- alsa-base
- alsa-utils

I tried running sudo alsaconf but i got "command not found"](*,) 

Help please:-k

---

### Post by Kristopher on 2006-10-22
Little update, i just installed 6.06 as VM on my friends PC and he is on the same boat and tried what i did and the same result.

---

### Post by Kristopher on 2006-10-22
WOOHOO am learning

Did this sudo dpkg-reconfigure xserver-xorg and hit enter for all apart from the keyboard i put "uk" and put a "x" for 1024 res now for the audio.

---

### Post by raul_ on 2006-10-22
try to install "alsamixergui". That should take care of some dependencies

---

### Post by Kristopher on 2006-10-22
Tried in the SPM but didnt show up and also at teminal

"sudo apt-get install alsamixergui" - Couldnt find package](*,)

---

### Post by raul_ on 2006-10-22
You'll have to enable the extra-repositories. Take a look at this guide
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by Kristopher on 2006-10-22
Function "snd_ctl_open" failed for default: no such device:confused:

---

