---
title: "Screen resolution problem"
date: 2008-01-08
forum: General Help
---

### Post by Bunky on 2008-01-08
I was using the "sudo dpkg-reconfigure -phigh xserver-xorg" command to attempt of fix a problem with my new monitor and now I've lost my higher resolutions. How do I get them back? All I have at present is:-

[*] 1024x768                                            
[*] 800x600                                                 
[*] 640x480

---

### Post by LoungeLizard362 on 2008-01-08
In my experience, if you do it without -phigh in the command it will give you the full range of resolutions

give this a try:

sudo dpkg-reconfigure xserver-xorg

hope it helps

---

