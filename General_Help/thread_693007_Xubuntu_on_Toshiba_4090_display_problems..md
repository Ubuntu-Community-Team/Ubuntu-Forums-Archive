---
title: "Xubuntu on Toshiba 4090 display problems."
date: 2008-02-10
forum: General Help
---

### Post by gofes on 2008-02-10
Hello.

I have an old old (about 1999) Toshiba laptop. I have Xubuntu installed but the bottom 5th of the screen has fuzzy lines across it.

[IMG]http://www.dylansicecream.co.uk/photos/1.jpg[/IMG]

[IMG]http://www.dylansicecream.co.uk/photos/2.jpg[/IMG]

I did have Ubuntu (7.04) on the laptop, which caused the same problem, but it solved it by changing the display driver from trident  to  vesa  in xorg.conf

Now changed to xubuntu,  got the same lines, but now I can't get rid of them. When I change  xorg manually or through  ```
sudo dpkg-reconfigure xserver-xorg
``` it causes the computer to freeze at the final stages of loading Xubuntu. 

Am I going about this the right way, or does anyone have any suggestions.

Thanks

---

### Post by NineKnuckles on 2008-02-28
Hey there gofes, I think I've got the same the problem as you.  I recently installed Xubuntu 7.10 on my old 4090CDS just to mess around and stuff, and I have the exact same problem.
   Even though I'm very new to Linux, I think I have a temporary fix, found by searching a few forums (including this one).  I had to change the pixel depth in a 'xorg.conf' file.  Unfortunately, this increases the size of the band, but it doesn't cover active windows, just the desktop (So I can now read a whole page of text, instead of seeing the band after-image at the bottom).
   Like you I tried changing the display driver to vesa, but that totally messed things up - I couldn't even get past the splash screen.  I managed to get back to 'trident' and have settled with the previously mentioned work-around.
    So what worked for me is changing 'Defaultdepth' from 24 to 16 in the "Monitor" section, of xorg.conf.  By no means is this a full fix, as I'm still trying to find a way to fully fix this too, just thought it might help.

   Sorry if that was a bit long winded

   P.S - Literally 1 week into Linux, so this may not have the same result for you ( I tried a few things people suggested in the past which had v. different results for me).  I only mention this because you wrote that you are running Xubuntu 7.04

---

