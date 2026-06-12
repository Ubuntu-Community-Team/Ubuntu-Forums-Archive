---
title: "how update bios driver?"
date: 2012-12-30
forum: General Help
---

### Post by Chogan on 2012-12-30
i read some where that updating bios driver is possible and useful.
how can i update my hp pavilion dv2500 notebook bios using ubuntu 12.04?

---

### Post by Mark Phelps on 2012-12-30
I don't know where you read that ... but there is no such thing as a "BIOS driver" ...

You should NOT even attempt to update your BIOS unless, (1) there is something specific that the new BIOS version provides or (2) there is a specific problem that the new BIOS version fixes.

You need to check the documentation that came with your Notebook and see what it says about doing BIOS updates. There are generally done one of two ways.  First, using a utility that runs in MS Windows.  Second, using some special key combination that boots you into an environment that allows you to update the BIOS.

If you don't have either of these -- leave it alone!  IF you make a mistake trying to do this, you will end up with an expensive electric "brick".

---

### Post by Wim Sturkenboom on 2012-12-30
> **Chogan said:**
> i read some where that updating bios driver is possible and useful.
There is no such thing as _bios driver_ ;) Yes, it's possible. No, it's not usefull unless something does not work that can be blamed on the BIOS or there is new functionality in the BIOS that you really can't live without.

> **Chogan said:**
> 
how can i update my hp pavilion dv2500 notebook bios using ubuntu 12.04?Check the HP website if there are linux tools available for Ubuntu. Check the user manual of the machine to see what is required; if you're lucky there can be some kind of functionality in the BIOS to do the upgrade.

---

### Post by rnerwein on 2012-12-30
> **Chogan said:**
> i read some where that updating bios driver is possible and useful.
how can i update my hp pavilion dv2500 notebook bios using ubuntu 12.04?
hi
!!!!!!!!!!!! listen to Mark Phelps post (especially the last sentence) !!!!!!!!!!!!!!!!!!!
cheers

---

### Post by Pjotr123 on 2012-12-30
Flashing BIOS is risky, that's true. But I always do it, because of an irrational reason: it makes me feel like I have a new piece of hardware. :biggrin: 

In all the years that I've flashed BIOS'es, only one motherboard was bricked because of it. And I've flashed hundreds of times....

So the risk is not great, provided that you do it carefully.

---

### Post by Frogs Hair on 2012-12-30
Methods vary by motherboard see the documentation as Mark suggested. Unless the update addresses issues with your current hardware there is no need.

---

### Post by grahammechanical on 2012-12-30
I have been using this self-built desktop for five years. I have never flashed the BIOS. I have not had the need. But I can tell you this, I have yet to see an ASUS utility that will let me flash the BIOS in Linux. ASUS has given me utilities to do it in Windows and even from DOS but not from Linux. So, if I do ever flash the BIOS I will have to do it using the DOS floppy disk utility that is on the ASUS drivers CD.

Regards.

---

### Post by Pjotr123 on 2012-12-30
> **grahammechanical said:**
> I have been using this self-built desktop for five years. I have never flashed the BIOS. I have not had the need. But I can tell you this, I have yet to see an ASUS utility that will let me flash the BIOS in Linux. ASUS has given me utilities to do it in Windows and even from DOS but not from Linux. So, if I do ever flash the BIOS I will have to do it using the DOS floppy disk utility that is on the ASUS drivers CD.

Regards.

You can use a memory stick + Unetbootin + FreeDOS for that. Did it many times like that; works fine. No need for Windows. :)

---

### Post by Cheesemill on 2012-12-30
> **Pjotr123 said:**
> You can use a memory stick + Unetbootin + FreeDOS for that. Did it many times like that; works fine. No need for Windows. :)
+1 That's the method I use on some of my machines.

On newer machines there is often a key you can press when you boot (it's End on my Giga-Byte mobo) to flash directly from a BIOS image saved to a USB drive, thus removing the need for Windows or DOS altogether.

---

