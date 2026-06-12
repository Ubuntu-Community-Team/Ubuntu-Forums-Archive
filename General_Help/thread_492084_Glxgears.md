---
title: "Glxgears ??"
date: 2007-07-04
forum: General Help
---

### Post by TobbeR on 2007-07-04
Hi all
Please explain glxgears to me, I have finally succeeded in installing 3D on my Radeon 9250 and now have direct rendering. When I test it with glxgears it will show ca 2000 fps 
but if I leave it alone for a while it rises to around 10.000 after 1-2 minutes. What happens after 2 minutes? I followed a guide by Darkoz, at first with no success but it turned out to be a setting in my bios limiting graphics memory to 64 mb. As soon as I changed that 3D was ok.
TobbeR

---

### Post by christhemonkey on 2007-07-04
Maybe whatever copmutations it needs to do are completed after 1 or 2 minutes so the animation just gets rendered over and over?

---

### Post by greg_g on 2007-07-04
You got your 9250 to work??

Could you post the steps you used to do so?

Thanks

greg

PS: I was in Edgy I had a 9250.  Couldn't get 3d for the life of me.  But I haven't tried since then, that box has been in the corner thinking about its problems. ;)

---

### Post by TobbeR on 2007-07-04
Hi Greg
Not to complicated, I just followed this thread: [http://ubuntuforums.org/showthread.php?t=462823&highlight=9250](http://ubuntuforums.org/showthread.php?t=462823&highlight=9250), BUT, it didn't work at first. I have a ASUS mb and in the bios there are some settings concerning AGP. 
I played with them for a while and I think it was the graphics memory that was wrong, it showed only 64 mb but my 9250 has 256 mb. Changed that and changed the AGPmode to 4x and then 8x, both worked. There is something called AGP Control and I enabled it but don't know if it's important. I did try fglrx first but AFAIK it will not work with Xorg 7.2.
Good luck
TobbeR

---

### Post by greg_g on 2007-07-04
Thanks TobbeR, maybe I can get that system going again.

---

