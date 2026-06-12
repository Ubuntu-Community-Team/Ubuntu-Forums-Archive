---
title: "Remote Desktop password length"
date: 2006-11-09
forum: General Help
---

### Post by btboudreaux on 2006-11-09
Why is the password for remote desktop limited to 8 characters?? Can this be changed? I would think something that allows other people to access your machine from anywhere in the world would allow a stronger password.

---

### Post by sethmahoney on 2006-11-12
> **btboudreaux said:**
> Why is the password for remote desktop limited to 8 characters?? Can this be changed? I would think something that allows other people to access your machine from anywhere in the world would allow a stronger password.

Yeah, that does seem remarkably stupid...

---

### Post by commonplace on 2007-04-22
I came across several threads with this as the question, but none had answers. Anyone out there know of a way to set a longer password for the remote desktop (VNC) feature that's included with Ubuntu? I thought maybe, just maybe, it'd have been changed in 7.04... but no, it still has the same eight-character limit on the password. It seems amazing that a system touted as being secure (Linux) would have their default remote desktop feature have a password limit not on how SHORT the password cannot be, but rather, how LONG it CAN be. Very weird.

/Kevin

---

### Post by engla on 2007-04-22
Probably, it can't be changed that easily.. if it's set to 8 characters, then the password technology used there only uses a maximum of 8 characters.. so a patch to allow longer would not make them more secure (any password over 8 chars would be truncated!). So it has to come to a larger change in the VNC code.

---

