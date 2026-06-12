---
title: "Quick note on burning .nrg dvd images"
date: 2005-08-20
forum: General Help
---

### Post by OneSeventeen on 2005-08-20
so far, *every single* .nrg dvd image file I have copied in ubuntu has been done with this method:

mv my_movie.nrg my_movie.iso

then in nautilis, right-click my_movie.iso and it works!

I tried using nrg2iso but all of the .nrg files were already ISO format!

Hope this helps save a headache for those of you switching from windows nero to linux whatever...

---

### Post by Non Plus Ultra on 2008-01-23
I don't think tjhat&#347; entirely true. It's worth trying, but sometimes you need nrg2iso. No problem there, it's quick and easy to use. Just type
sudo apt-get install nrg2iso

and after installation:
nrg2iso image.nrg image.iso

all set and done :)

---

### Post by danwood76 on 2008-01-23
Yeah this wont work with true .nrg files.
This is due to nrg basically having a header before the ISO, so its more of an offset ISO.
You can DD the ISO out of the nrg but using nrg2iso is much easier then searching for the offset manually.

regards,
Danny

---

