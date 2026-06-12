---
title: "How do I know my graphics card is working properly?"
date: 2006-10-22
forum: General Help
---

### Post by dboot on 2006-10-22
Is there a series of tests I could run to see if I've enbled everything I can enable on my graphics card? After installing the latest drivers, I still don't feel like I can do as much with my GC on Ubuntu that I can do on my Windows partition. There is more to "tweak" in my Windows partition with the extra nvidia programs.

I have an nvidia 6800 GT OC with the latest nvidia drivers (at least, I think the latest drivers). I've set up dual screens, XGL, and Beryl with no difficulty, but when I try to play Linux based graphic intensive games (with one screen, and with xgl and Beryl turned off) I get horrible frame rates. As of right now, I get an error when I play the games with XGL and Beryl turned on. Should I or will I ever be able to play the game with XGL and Beryl installed?

I'm honestly not sure what I should be able to do with my graphics card.

Thanks!

---

### Post by dboot on 2006-10-23
/bmp

---

### Post by madmetal on 2006-10-23
to check if 3d acceleration is on open a terminal and run 
glxinfo | grep direct
if the answer is yes then 3d acceleration is on..

---

### Post by dboot on 2006-10-24
What if 3d acceleration isn't on? Is that something I have to enable or is it something my graphics card might not have?

I found [this thread]("http://www.ubuntuforums.org/showthread.php?t=176636") after searching 3d acceleration.

---

### Post by Bloch on 2006-10-24
I too have also often wished there was some profiling / testing software for ubuntu linux.

I get fed up seeing glxgears mentioned. Surely someone could write a little opengl application where people could SEE that their cards are working directly?

---

### Post by dboot on 2006-10-24
> **Bloch said:**
> I too have also often wished there was some profiling / testing software for ubuntu linux.

I agree. I'd like someway to compare my setup to my capabilities according to my hardware.

---

### Post by dboot on 2006-11-01
Anything new with Edgy?

---

