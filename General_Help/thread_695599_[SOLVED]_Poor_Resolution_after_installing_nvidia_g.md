---
title: "[SOLVED] Poor Resolution after installing nvidia graphics card"
date: 2008-02-13
forum: General Help
---

### Post by sourabhsharma149 on 2008-02-13
Hello Friends,

I am having Gutsy on Dell inspirion 6400 and nvidia GEForce 7300 graphics card.

I configured my graphics card by driver available for  ..It ran fine.

but in next reboot it stuck at rc.local  and switched to poor graphics automatically..please mind that by reinstalling driver again good graphics restored and in next reboot it stucked again..please someone help...

Thanks

---

### Post by Crooksey on 2008-02-13
Did you run 

```

nvidia-xconfig
```

This will optimise your xorg.conf file to work with the NVIDIA drivers.

---

### Post by kpkeerthi on 2008-02-13
Can you try [this]("http://ubuntuforums.org/showpost.php?p=4322584&postcount=3") ?

---

### Post by BobLand on 2008-02-13
Crooksey,
Great timing.  This fixed the driver problem on my wife's computer.

Thanks,
bobland

---

