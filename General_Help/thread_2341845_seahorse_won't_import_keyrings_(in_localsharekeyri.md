---
title: "seahorse won't import keyrings (in local/share/keyrings or not)"
date: 2016-11-01
forum: General Help
---

### Post by subterra on 2016-11-01
I'm trying to import a backup of my seahorse passwords and it won't work.

I  have copies of the contents of .loca/share/keyrings, including  EXAMPLE.keyring.  I used to be able to simply place a backup like  EXAMPLE.keyring into .local/share/keyrings and seahorse would pick it  up.  That isn't working anymore.  I also tried file->import in  seahorse but got an error message that:

Could not display 'EXAMPLE.keyring'
Reason:	Unrecognized or unsupported data.

I  originally created these keyrings using an old version of seahorse, so I  tried reinstalling that same version, but this still fails.  Oddly  enough, I also created a new password keyring in seahorse, TEST.KEYRING,  then move it out of .local/share/keyring and deleted it from seahorse;  when I tried to import this one, which should definitely work, that also  failed (placing it back in the folder failed, and using file->import  failed).  Any idea?

Thanks a lot.

---

