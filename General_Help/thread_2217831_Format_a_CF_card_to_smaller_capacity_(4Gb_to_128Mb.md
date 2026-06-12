---
title: "Format a CF card to smaller capacity (4Gb to 128Mb)"
date: 2014-04-18
forum: General Help
---

### Post by spacemen12 on 2014-04-18
Hi,
    I want to do something that seems weird, but here it is. I have a old camera that I gave to my "really young" daughter. The camera can only take cf card smaller or equal than 128mb. I don't have such card, but I have a few 4gb that I could let her use. 

    Is there a way to format the card in the computer so that when I put it in the camera it shows that it is a 128 mb card. I don't mid if the only space available is 128 mb. It is an old camera and max size if 1Mb anyway.

Best regards,

---

### Post by coldcritter64 on 2014-04-18
I don't know if this suggestion will work, I suspect not. You could try putting a ~ 120 MB partition at the front of the CF card and see it the camera recognizes it. 

Either use gparted off a live cd or alternatively install gparted to your installation for doing such jobs. Once the partition is made then format it in the manner the camera needs (I'd guess that would be a FAT style partition, though I have no idea what filesystem your camera actually uses). Insert the card into the camera and check if it works. 

This suggestion is a bit of a "wild shot". Whether it works or not depends on the cameras functionality/design.

---

