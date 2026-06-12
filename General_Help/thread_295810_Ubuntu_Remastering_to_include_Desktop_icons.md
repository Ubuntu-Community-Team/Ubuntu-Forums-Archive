---
title: "Ubuntu Remastering to include Desktop icons"
date: 2006-11-08
forum: General Help
---

### Post by Grim_b on 2006-11-08
Hi,

I have a need to create an install that will include desktop icons from all the OpenOffice applications from first boot (ie thier not there on the default install)

The reason for the question is that I have 200+ machines to do and am looking to avoid having to signon and setup these icons after each install.

I have created a script to create them for me, but remastering would mean I can tweak things and create a custom / slimline install.

Any links to relivant material would be cool as well as discussion of other options is welcome.

Ideally I would like to use a partition image like I could in partition magic from the the windows age, but seeing as I am in linux now it seems too backward to do that.

Thanks in advance,
Grim.

---

### Post by K.Mandla on 2006-11-08
I moved your thread into General Help, where it should get more attention.

You might want to look into the [Reconstructor]("http://reconstructor.aperantis.com/"), which allows you to build customized live CDs. I don't know if it will help if you want a full installation.

It might also be possible to do this with the debconf preseed stuff (which I think is more or less like an unattended installation in Windows), but I've never done it. Don't hold me to that.

Would this be any kind of candidate for a network installation?

---

### Post by Grim_b on 2006-11-13
Hi K.Mandla,

Sorry for the delay in replying,  I downloaded and tried the reconstructor and managed to create a livecd.  This however did not keep my desktop icons when installed?

Do you know if I need to (or can) make my icon set for the desktop a module and include it in the reconstructor setup?

As for the network install, yes I would like to investigate this but I really need an installation that will include my personal settings in the build.

If anybody else knows of a way to remaster Ubuntu with personal icons on the desktop, I would like to hear from you.

Thanks again all,

Grim.

---

### Post by Grim_b on 2006-11-17
I have now looked into the "remastering ubuntu dapper" (do a google) and have now got to a point where I am looking to create a custom install that can be rolled to 200+ CPUs for remote install.

Thanks again.

---

