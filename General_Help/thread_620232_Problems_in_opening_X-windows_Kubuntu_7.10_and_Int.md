---
title: "Problems in opening X-windows: Kubuntu 7.10 and Intel DG965"
date: 2007-11-22
forum: General Help
---

### Post by omegacentauri on 2007-11-22
Hello,

I am a new Ubuntu user, and just installed Kubuntu 7.10 on a new desktop 
with an Intel Core Duo Processor and an Intel DG965 motherboard with 
Graphic Media Accelerator (GMA) X3000. 

I have problems with many programs which open X-windows to display 
plots or images (IDL, fv, and other packages to process FITS files).
The problems are slightly different for different programs, but they might 
be related to the same bug. I report the problems below.

- With IDL, the problem is a "segmentation fault (core dumped)",
  followed by a crash of IDL, whenever I try to open a window with the 
  command "window". 
  This bug can be fixed by adding this line in my ".bashrc" file:
  export LIBGL_ALWAYS_INDIRECT=1
  as suggested in the IDL Tech Tip number 4177:
  [http://www.ittvis.com/services/techtip.asp?ttid=4177](http://www.ittvis.com/services/techtip.asp?ttid=4177)
  I still reported the bug here to give a complete overview of the problem 
  (and to help any other user who has the same problem).
- With the FITS viewer "fv", the problem is that the FITS file is correctly read
  (the relevant fv-table with the numbers of the image photon counts is correct), 
  but the image is displayed as a flat image with zero counts in each pixel.
  The image is then properly read, but not properly displayed.
- With another (non-standard) program for FITS processing, the image is 
  again displayed as without any colour contrast (i.e. as a black window), 
  although the cursor which browses the image can read the correct count 
  variations from pixel to pixel. 

Moreover, when running all these programs on this pc remotely from another pc, 
all the windows are opened in a proper way. 

I suspect there is a problem with the X server of my pc, but I am not sure.
If this is the case, how can I fix it?

Attached you can find my /etc/X11/xorg.conf , in case this can be of any help.

Any suggestion is most welcome! 

Thanks a lot!

---

