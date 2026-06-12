---
title: "VPC 2007 Sound Card... Any way to fix this?"
date: 2007-04-14
forum: General Help
---

### Post by Ikith on 2007-04-14
So I have the full install working updates and all... Well almost all... I was wondering if there was a way to make the sound work... It seems to pick up the sound card but but when I try to access the volume settings or play any sound it gives me an error about no stream. Any way to fix this?

BTW, I'm 100% new to Ubuntu and VPC :-P! But everything seems to be going well.

[IMG]http://i17.photobucket.com/albums/b69/DarkenedSkeleton/1.jpg[/IMG]
[IMG]http://i17.photobucket.com/albums/b69/DarkenedSkeleton/2.jpg[/IMG]
[IMG]http://i17.photobucket.com/albums/b69/DarkenedSkeleton/problem.jpg[/IMG]

---

### Post by harishvja on 2008-01-06
mee too having the same problem what i got from the sources is vpc gives emulated sound to ubuntu which is of isa sb16 .i tried in many ways but unable to get the sound if any one had fixed the problem can you please post it

---

### Post by bennyj on 2008-01-10
sudo gedit /etc/modules

add the following

snd-sb16

hit return after entering the above

save the file

reboot

---

