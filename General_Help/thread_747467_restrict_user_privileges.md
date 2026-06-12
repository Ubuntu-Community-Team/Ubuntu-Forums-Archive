---
title: "restrict user privileges"
date: 2008-04-06
forum: General Help
---

### Post by boondocks on 2008-04-06
I want to create a guest account on my Ubuntu system for visiting relatives.
But I want to limit their privileges.

Assuming they have a "/home/guest" directory.

They should be LIMITED to:
[LIST]
[*]the "/home/guest" directory
[*]download/upload files
[*]ssh/scp in/out of the system
[*]fixed quota on "/home/guest"
[/LIST]So I basically want to confine them to their guest room.

Is there an admin tool that will help me enforce this?

---

### Post by leonidas666 on 2008-04-06
> **boondocks said:**
> 
They should be LIMITED to:
[LIST]
[*]the "/home/guest" directory
[*]download/upload files
[*]ssh/scp in/out of the system
[*]fixed quota on "/home/guest"
[/LIST]So I basically want to confine them to their guest room.


Just create a user named "guest". In Kde there's a gui for it in the system setting, in gnome there's probably something in the "system" menu.The new user will be restricted to the home directory automatically, but if you don't want the guest to read or write to the other user's directoy, you'll have to set the file permissions for /home/userx to the desired values (the other users can do this by themselves).
For the quota there's probably some way to do it (maybe search for "quota" in synaptic?), but are you sure that you need that? Are you so low on disk space? Or are your relatives so abusive with your machine :)

---

### Post by boondocks on 2008-04-06
It is more than just protecting other user's home directories.
For example, I don't want the guest to view the system files in /etc and other such directories.

I am not low on disk space.
Since I want them to have scp/ssh access, I want to make sure the sandbox has a practical size.  (Say 5 Gb.)

That way if the "visiting" guest needed more than 5 Gb, he would have to justify it.

---

### Post by hyper_ch on 2008-04-06
but you still want to give them physical access to the machine?

---

### Post by boondocks on 2008-04-07
Yes. I do.
Besides, it would be good to have this level of protection on the system in any case.
I would like to give access to this system to a few visiting relatives as long as I can have a bit of a safety net in place.

---

### Post by hyper_ch on 2008-04-08
if you want to give them physical access they can boot into recovery mode or use a live cd... and then all your precautions are useless anyway...

Either trust them or don't give them physical access...

---

