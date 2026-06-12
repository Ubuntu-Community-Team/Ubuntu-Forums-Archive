---
title: "How do I swap the Caps Lock key and the Ctrl key in Kubuntu"
date: 2006-11-17
forum: General Help
---

### Post by void1 on 2006-11-17
Hello and thanks for the help.

How do I swap the keyboard locations of the Caps Lock key and the Ctrl key in Kubuntu 6.10 Edgy?

In Ubuntu 6.10 Edgy, I do the following:
 System->Preferences->Keyboard
 Layout Options->Ctrl key position->Swap Ctrl and CapsLock.

Unfortunatley, I can't find this option in Kubuntu 6.10 Edgy.

I've found instructions on how to do this for Ubuntu ([http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_remap_the_Caps_Lock_key_as_another_Control_key)](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_remap_the_Caps_Lock_key_as_another_Control_key)), and Xubuntu ([http://ubuntuforums.org/showthread.php?t=247470)](http://ubuntuforums.org/showthread.php?t=247470)), but not for Kubuntu; and the Ubuntu/Xubuntu instructions don't work for Kubuntu 6.10.](*,) 

So how do I swap the locations of the caps lock and ctrl keys in Kubuntu 6.10 Edgy?

Thanks.

---

### Post by hal10000 on 2006-11-17
Hi void1

in kubuntu you can use the kcontrol progeam to change your keyboard-settings.
Just type <ALT>+<F2> ant type in kcontrol to launch the controlcenter.
Here you type in the search-field (on the top-left) layout and in the bottom-left you choose "keyboard layout" (I have to guess what the English expression is, because my settings are in german)
On the right you should then see the keyboard-layout; you have to move to "Xkb-Optios" and activate xkb-optins (on the top). Then you scroll down and can find the point where to swap CTRL and lock Keys.

---

### Post by void1 on 2006-11-17
It worked!
Thanks for the help.

---

