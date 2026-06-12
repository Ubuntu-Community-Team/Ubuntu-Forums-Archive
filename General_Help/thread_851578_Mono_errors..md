---
title: "Mono errors."
date: 2008-07-06
forum: General Help
---

### Post by BeanBeamer on 2008-07-06
When I try to run the NRPG Ratiomaster with mono, I get the following errors:```

mono '/home/bean/Desktop/NRPG.exe'

** (/home/bean/Desktop/NRPG.exe:20886): WARNING **: The following assembly referenced from /home/bean/Desktop/NRPG.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/bean/Desktop).


** (/home/bean/Desktop/NRPG.exe:20886): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (/home/bean/Desktop/NRPG.exe:20886): WARNING **: Missing method EnableVisualStyles in assembly /home/bean/Desktop/NRPG.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'
```

What could be wrong and how do I fix it?

---

### Post by mianda_psi on 2008-07-07
I also get the same problem when I try to run AniMplayer using mono.  This is what i get:

```
** (Lycoris.exe:13030): WARNING **: The following assembly referenced from /home/jeff/NMC/Lycoris.exe could not be loaded:
     Assembly:   System.Windows.Forms    (assemblyref_index=0)
     Version:    2.0.0.0
     Public Key: b77a5c561934e089
The assembly was not found in the Global Assembly Cache, a path listed in the MONO_PATH environment variable, or in the location of the executing assembly (/home/jeff/NMC/).


** (Lycoris.exe:13030): WARNING **: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.

** (Lycoris.exe:13030): WARNING **: Missing method EnableVisualStyles in assembly /home/jeff/NMC/Lycoris.exe, type System.Windows.Forms.Application

Unhandled Exception: System.IO.FileNotFoundException: Could not load file or assembly 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089' or one of its dependencies.
File name: 'System.Windows.Forms, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089'
```

Any help would be appreciated.

---

### Post by Seventh on 2008-08-26
I think you'll need to install the libmono-winforms1.0-cil and/or libmono-winforms2.0-cil packages in synaptic to use System.Windows.Forms.

---

### Post by tehtrk on 2008-09-19
[CENTER][B]OOPS!
[/B][/CENTER]
 
Hey guys, if you're like me and want to use the Evolution plugin for Gnome-do, then the problem is easily remedied with:

```
sudo apt-get install libevolution3.0-cil
```The problem is that it's missing a MONO assembly for Evolution, as stated in the errors given when you try to run Gnome-Do without it. More info can be found here:

[https://bugs.launchpad.net/do/+bug/254350](https://bugs.launchpad.net/do/+bug/254350)

HTH,


JP

---

### Post by furthur on 2008-12-06
Thanks! that solved it for me.

---

### Post by directhex on 2008-12-06
> **Seventh said:**
> I think you'll need to install the libmono-winforms1.0-cil and/or libmono-winforms2.0-cil packages in synaptic to use System.Windows.Forms.

2.0 - If you look at the error, you see "Version:    2.0.0.0"

---

### Post by mingz4 on 2010-01-06
> **directhex said:**
> 2.0 - If you look at the error, you see "Version:    2.0.0.0"
Thanks. It solved my problem with KeePass

---

### Post by mrdejong on 2011-09-15
> **Seventh said:**
> I think you'll need to install the libmono-winforms1.0-cil and/or libmono-winforms2.0-cil packages in synaptic to use System.Windows.Forms.

Thx... it helped me to run KeePass!

---

### Post by directhex on 2011-09-16
> **mrdejong said:**
> Thx... it helped me to run KeePass!

Keepass2 packages are already in Ubuntu, and handle dependencies for you

---

### Post by PayPaul on 2011-09-20
:confused:I have a baby question and hope that someone with experience and good communication can explain. What is Mono? I saw a thread on another section that mentioned Ubuntu's dependence upon Mono. I didn't quite understand the reasoning or the problem presented by the OP in that thread. Mono also appeared to have some connection with Gnome or related to gnome. It seems to me from the context of this thread it's something like Wine.

---

### Post by directhex on 2011-09-20
> **PayPaul said:**
> :confused:I have a baby question and hope that someone with experience and good communication can explain. What is Mono? I saw a thread on another section that mentioned Ubuntu's dependence upon Mono. I didn't quite understand the reasoning or the problem presented by the OP in that thread. Mono also appeared to have some connection with Gnome or related to gnome. It seems to me from the context of this thread it's something like Wine.

It's a free software development framework which provides a C# and VB.NET compiler. It's used for some GNOME apps like Banshee and Tomboy, but rarely for KDE apps.

---

### Post by tux-gamer on 2011-10-05
I Just wanna to say thanks.
I Have problem running Subtitle Edit ( [http://nikse.dk/Home/Details/634412577440000000](http://nikse.dk/Home/Details/634412577440000000) )
After installing mono-winforms, it could run. :D

---

