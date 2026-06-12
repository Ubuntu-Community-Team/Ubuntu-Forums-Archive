---
title: "GRUB2/Grub Customizer background problem"
date: 2013-06-25
forum: General Help
---

### Post by Nick Fane on 2013-06-25
I have been successfully using Grub Customizer under Peppermint3 (based on Lubuntu 12) but have now upgraded to PM4 (based on Lubuntu 13.04). This change also moves from Grub 1.99 to 2.00 (the nomenclature is confusing - both Grub2??)
 Every time I load GC using the same information I had used previously, and importantly the same background file, the image does not appear on the GRUB screen when I re-boot and when I re-enter GC the image file link has been deleted from GC.
 The revised menus are working, but the Font selection is unreliable and of course the font colours do not work (as expected when there is no background image).
 I have repeated this process a number of times on 4 separate (and different) laptops and am getting the same problem on them all. The background file is a .png and resolution 640x480 - I had previously been round the loop with G1.99 of ensuring that the file was suitable. Can anyone advise me if the requirements for a background file have changed from Grub1.99 to 2.00, or any other suggestions as to why the relatively simple actions no longer work?

---

### Post by Nick Fane on 2013-06-25
Well, I think I have finally solved this myself!
Various suggestions included: the file might need to be .tga; the file must be in \root; the file must be in \boot\grub
The file may need to be in \boot\grub if just using 'sudo update-grub' rather than GC, but the main reason turns out to be the FILENAME - it must NOT have any SPACES - simple as that. My .png file now works fine. I'd now mark this as 'solved' if the 'Thread Tools' gave me the option as per the FAQs.

---

### Post by Nick Fane on 2013-08-15
On another attempt I've marked it 'solved'!

---

### Post by Paddy Landau on 2014-05-06
Who would have guessed!

I have been using a file with spaces for months without problem. But now, I have installed 14.04 on another machine, and removing the spaces solved it. How weird!

---

