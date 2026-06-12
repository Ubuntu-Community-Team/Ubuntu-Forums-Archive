---
title: "Conky Seamod displays on top of user windows on GNOME Session Fashback"
date: 2017-06-09
forum: General Help
---

### Post by ubix on 2017-06-09
Hi everyone!

After upgrading from Ubuntu 14.04 to 16.04, my Conky setup got broken in numerous  places. With the help of you and other folks on the net, I've been rather successfully fixing it now for about two days. However, as stated in the title of this post there is one problem that persists. Namely, **Conky Seamod displays on top of user windows in _GNOME Session Flashback_**.

This problem was caused after trying to fix transparency problems, following the instructions found in  [https://askubuntu.com/questions/447977/why-isnt-conky-working-right-in-unity-desktop](https://askubuntu.com/questions/447977/why-isnt-conky-working-right-in-unity-desktop) - the relevant parts of this link I am also posting here for your convenience, which I am including in the following quote: 

> When **"own_window_type override"** is used the distortion is caused. Now to clear the distortion one may use **"own_window_type desktop"** in the .conkyrc instead of **"own_window_type override"**. But this causes other problems like disappearance of conky when trying to work in the desktop (i.e right clicking, opening a menu from panel etc.). Therefore instead of **"own_window_type override"** one may use **"own_window_type dock"**. This won't let the conky to disappear when working on the desktop. Also to solve transparency issue one may remove the line **"own_window_transparent yes"** and then include the following lines in its place:

		own_window_argb_visual yes    
		own_window_argb_value 0

As I said, I modified my ".conkyrc" (conky_seamod) file following the above quote. Following is the code segment and the pertinent lines in my seamod config file, after all the changes made to address transparency problem which created the persistent problem mentioned in the title of this post:
> own_window yes

# -- transparency problem in 16.04 (Fri 09 Jun 2017 08:29:05)
#own_window_type normal
#own_window_type desktop
#own_window_type override
own_window_type dock
#own_window_transparent yes

own_window_argb_visual yes
own_window_colour 000000
own_window_argb_value 0
own_window_hints undecorate,sticky,skip_taskbar,skip_pager,below
Thx in advance.

---

### Post by #&amp;thj^% on 2017-06-09
Change this "own_window_type dock"
To "own_window_type normal"
Any better?

---

### Post by ubix on 2017-06-09
That is not an option for me. It causes troubles with transparency, also, text in Seamod becomes unintelligible shortly after I start screwing up with this parameter. Worse, setting  **"own_window_type normal"** in GNOME Session Flashback displays Seamod in its own window with decorations, which is unacceptable.

---

