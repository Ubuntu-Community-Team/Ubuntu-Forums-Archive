---
title: "grub error 22"
date: 2008-02-25
forum: General Help
---

### Post by Hawk__0 on 2008-02-25
My girlfriend wants to get rid of ubuntu (wireless issues), and while in windows i told her to format the drive without even thinking (in disk management).  I completely forgot about grub now grub hates us. lol.

I am telling her to try this for now: [http://tinyempire.com/notes/files/fixntldriso.zip](http://tinyempire.com/notes/files/fixntldriso.zip)
since it will apparently install NTLDR, but will that overwrite grub and all... or do i have to do something else?

---

### Post by rollinroll on 2008-02-25
You could reinstall windows as it will owerwrite the MBR.

---

### Post by Hawk__0 on 2008-02-25
lol, no.  thats a waste of time and data loss.  this is my GF here, "i need my things" and shes long distance, so over the phone this SUCKS. haha.  No resources (CD-Rs [well she has 2!], etc) so options are limited and i know this can be done :P

---

### Post by teryowen on 2008-02-25
boot with the windows CD.

and through it get to a command prompt and type:

either
fixboot C:

of

fixmbr

try those or look around for fixing mbr or fixing boot commands which should restore the mbr to boot windows.

---

### Post by slayer04 on 2008-02-25
> **teryowen said:**
> boot with the windows CD.

and through it get to a command prompt and type:

either
fixboot C:

or

fixmbr

try those or look around for fixing mbr or fixing boot commands which should restore the mbr to boot windows.

Damn I was going to say the sme thing but you beet me to it, but yea I agree with him but if windows isnt installed on the C drive then when tying the command "fixboot C:" you need to change the C to what ever letter windows is on for it to work

---

### Post by Hawk__0 on 2008-02-26
problem with this is that shes a noob, she has no cds or anything.. lol.  So i instructed her to download ubuntu and open up a terminal and use grub :S
i believe its:
sudo grub
root (hd0,0)
setup (hd0)

so we will try this and see if it works i guess =\

---

### Post by yurtos on 2008-02-26
1) boot from windows xp cd
2) enter Recovery Console by pressing R when you get this option
3) select Windows installation (press 1)
4) enter administrators password
5) type 
fixmbr
hit Y if prompted to confirm overwriting Master Boot Record
you can also use "fixboot" command instead of "fixmbr", should do the same thing. 
6) once everything is finished, reboot the system, take out windows xp cd and collect the payment from your girlfriend for services :)

cheers

---

