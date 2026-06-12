---
title: "Custom USB action"
date: 2007-06-13
forum: General Help
---

### Post by rich86 on 2007-06-13
Don't know if this is in the right place..sorry if its not.

I want a make a script that automatically runs when i plug in a certain usb device, for example usb backup drive, or camera. I can probably make the script but how do i get it to automatically run on plugging in the device.
Hope that makes sense, please ask what i mean if it doesn't
Thank in advance

---

### Post by reclusivemonkey on 2007-06-13
I'm not sure about a camera, but I have a USB memory stick, on which is a executable file called autorun. In System --> Preferences --> Removable Drives and Media, I have "Auto-run programs on new drives and media" ticked and it automatically executes the autorun script. HTH

---

### Post by rich86 on 2007-06-14
ahr cunning, just tested it on usb stick, so technically i can put an autorun program on my camera as i think it sees that as a mass storage anyway and have it copy the file to where i want them in the right folders.

just of interest is there anyway t o force it to run in shell so i can use `read` to get inputs? or is there some other command i should use. suppose i could write it in C or something?
don't mind if you don;t know i will look into it more soon.

---

### Post by reclusivemonkey on 2007-06-14
> **rich86 said:**
> ahr cunning, just tested it on usb stick, so technically i can put an autorun program on my camera as i think it sees that as a mass storage anyway and have it copy the file to where i want them in the right folders.

Possibly, but my camera is not mounted exactly the same way as a USB drive, but there is certainly no harm in trying.

> **rich86 said:**
> just of interest is there anyway t o force it to run in shell so i can use `read` to get inputs? or is there some other command i should use. suppose i could write it in C or something?
don't mind if you don;t know i will look into it more soon.

Try adding "sh" or something like "rxvt" to your script? Or maybe use zenity? zenity is what I use in mine, it looks nice in Gnome =] C would be overkill IMHO, but then I am not a programmer.

---

### Post by rich86 on 2007-06-14
i found Xdialog as well i will see which one i find easiest to use. 
and it looks like i can get it working by putting an autorun.sh on my camera, i have already made one for the external drive backup its great, i really am loving the ease that linux can be customised, then again i never really tried in windows, mainly out of fear of it all blowing up in my face!

thanks for your help i will get on with making the other script soon.

---

