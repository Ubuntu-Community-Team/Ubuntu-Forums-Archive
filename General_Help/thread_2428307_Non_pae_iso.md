---
title: "Non pae iso"
date: 2019-10-02
forum: General Help
---

### Post by rsteinmetz70112 on 2019-10-02
I'm looking fro an non pae kernnel ISO to use for a project I'm working on.
Can someon please identify a more or less recent version of lubuntu I can use whihc still has repositories available?
I'm open to using another Linux flavor if I can find one.

---

### Post by mörgæs on 2019-10-02
Are you sure that you can't use a standard 32 bit PAE ISO? All Pentium M's support PAE though some of them need a little tweaking.

If you do need a non-PAE ISO I suggest [Bodhi Linux]("https://www.bodhilinux.com/w/selecting-the-correct-iso-image/").

---

### Post by Impavidus on 2019-10-03
If I remember correctly, support for non-PAE kernels in the Ubuntu family was dropped after Xubuntu 12.04. That means support ended in April 2015. You need another distro.

If you don't really need non-PAE, but still 32 bit, use Lubuntu 18.04 LTS. it has 18 months of support left, and that'll be the end for 32 bit in the Ubuntu family. Read this: [https://help.ubuntu.com/community/PAE](https://help.ubuntu.com/community/PAE)

---

### Post by rsteinmetz70112 on 2019-10-03
In my current project I'm working on some older computers. Some can be used with Lubuntu 18.04 LTS using the forcepae tweak that works great. Others can't and need a true nonpae kernnel. 

Does anyone know if Knoppix still has such a thind available? I couldn't find it on their website but there were hints about it.

---

### Post by sudodus on 2019-10-03
[This link updated May 2019](https://itsfoss.com/lightweight-linux-beginners/) may help you find some good alternatives.

---

### Post by tea for one on 2019-10-03
Would Antix be suitable for your project?

[https://antixlinux.com/blog/](https://antixlinux.com/blog/)

Best wishes

---

### Post by rsteinmetz70112 on 2019-10-04
Thanks Everyone,

The list has some distro which clearly support hardware old enough not have pae, othere are somewhat ambiguous. 
Antix clearly has nonpae kernels.

Looks like I've be downloading and testing some isos. 

Ultimately I'm looking for an iso I can put in any old computer and have a very good chance of working and which has a few modern tools in particular ddrescue, gparted and ntfs tools.

I'm going to make this thread solved

---

### Post by mörgæs on 2019-10-05
Good luck.

If you find interesting results you are more than welcome to add to the Old Hardware thread.

---

