---
title: "why wont gxine and vmware leave my alsamixer settings alone?"
date: 2005-08-31
forum: General Help
---

### Post by glandula on 2005-08-31
im getting fed up having to open alsamixer and go over the settings every time ive used gxine or vmware (xp). why wont they leave the settings alone? is there a way to lock the settings in alsamixer so other apps cant touch it?

---

### Post by dlpfmVfH on 2005-08-31
did you try : sudo alsactl store

I think the differents is, with normal user mode, you can change volumes...so can programs...cause they use the same rights...

if you use sudo (root-user) access...then only the root-user has the right to change it back...not the programs...

maybe it will help...

---

### Post by glandula on 2005-08-31
nope, gxine still messes with the pcm volume

---

### Post by dlpfmVfH on 2005-08-31
gxine has the option to remember the volume and set it...
maybe if you turn that option off...

I don't know I have gxine installed but it doesn't act up...

can you give me extra info...maybe something else messes thing up...

---

### Post by Haegin on 2006-03-11
Set the level of user experience to Advanced (or above presumably) and under audio on the volumes tab check the box to remember the volume and set the volume to 100. Now restart and it should work.

---

