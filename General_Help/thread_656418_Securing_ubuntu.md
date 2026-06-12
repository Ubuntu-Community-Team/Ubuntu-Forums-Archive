---
title: "Securing ubuntu"
date: 2008-01-02
forum: General Help
---

### Post by supershin on 2008-01-02
Taken from : [http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_are_the_basic_things_I_need_to_know_about_securing_my_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_are_the_basic_things_I_need_to_know_about_securing_my_Ubuntu)

What are the basic things I need to know about securing my Ubuntu

    * Ensure a password is set for BIOS 
    - Can someone over the net easily access the BIOS?  
             
    * Ensure interactive editing control for GRUB menu is disabled
    * Ensure history listing is disabled in Console mode
    * Ensure Ctrl+Alt+Del is disabled in Console mode
    * Ensure interactive option is set for remove, copy and move of files/folders in Console mode
     - Console mode is what exactly,using the terminal? Can someone over the net make use of these?

---

### Post by Fixman on 2008-01-02
> **supershin said:**
> Taken from : [http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_are_the_basic_things_I_need_to_know_about_securing_my_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Feisty#What_are_the_basic_things_I_need_to_know_about_securing_my_Ubuntu)

What are the basic things I need to know about securing my Ubuntu

    * Ensure a password is set for BIOS 

    Not really necesary, unless someone has psichical access to the computer (so they actually use the computer, don't hack it)

   >  - Can someone over the net easily access the BIOS?  
no
             
    > * Ensure interactive editing control for GRUB menu is disabled
    If you don't know what is it then don't mess with it, it can hardly wipe out your computer

   >  * Ensure history listing is disabled in Console mode [/CODE]
   Doubt its pretty useful doing that, unless you actually use console mode often, of cat important files on it

    [QUOTE]* Ensure Ctrl+Alt+Del is disabled in Console mode
   If you don't use console mode, its unnecesary

    > * Ensure interactive option is set for remove, copy and move of files/folders in Console mode
Really don't know mutch about using this one

>      - Console mode is what exactly,using the terminal? Can someone over the net make use of these?
Not exacly. To enter console more, you can press Ctrl+Alt+f<n>, where n is a number from 1 to 6 (press ctrl+alt+f7 to come back). You can also use console mode by using Ubuntu on single user mode and logging as root for maiteneance.

---

### Post by kellemes on 2008-01-02
> **supershin said:**
> 
    * Ensure interactive editing control for GRUB menu is disabled



You can password-protect Grub.

---

### Post by Fixman on 2008-01-02
> **kellemes said:**
> You can password-protect Grub.

How can someone with no psychical access do your computer access GRUB?

---

### Post by ~LoKe on 2008-01-02
Most of these are pretty pointless...if someone competent gets physical access to your computer, you're done.  It's a lot of extra hassle to do all this unless you expect someone to break into your house.

---

### Post by kellemes on 2008-01-02
> **Fixman said:**
> How can someone with no psychical access do your computer access GRUB?


He can't.

---

### Post by kellemes on 2008-01-02
> **~LoKe said:**
> Most of these are pretty pointless...if someone competent gets physical access to your computer, you're done.  It's a lot of extra hassle to do all this unless you expect someone to break into your house.


Indeed.. this is more about privacy control then protecting from pc-killers.

---

### Post by markp1989 on 2008-01-02
is there a way to set grub to ask for a password before displaying the OS list?

---

### Post by ~LoKe on 2008-01-02
> **markp1989 said:**
> is there a way to set grub to ask for a password before displaying the OS list?

[This](http://ubuntuforums.org/showthread.php?t=7353) is old but it should probably still work.

---

### Post by supershin on 2008-01-02
Thanks everyone.

---

### Post by ~LoKe on 2008-01-02
> **supershin said:**
> Thanks everyone.

You're very welcome!  Let know if you figure it out.

---

