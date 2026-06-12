---
title: "usb hard drive wont work anymore"
date: 2007-05-14
forum: General Help
---

### Post by nrg762 on 2007-05-14
I installed kubuntu 6.10 a few months back and used my external USB hard drive just fine without any problems. I upgraded to 7.04 and now the USB drive won't work. When I plug it in it reconizes the drive and asks me what I want to do. I select "open in new window" option but nothing happens. I went to the hard drive management section and found that it wasen't enabled, I enabled it and tried it again but now it says I ddon't have proper premission to view it. I went back and adjusted it so everyone can veiw, and modify it but it still does the same thing. I think it is enabled under root but i don't know how to enable it for me(the user) 
thanks

---

### Post by turbojugend_gr on 2007-05-14
Can you do this for me so we can make sure root has the priviledges toread/write on this drive?

In a terminal issue the command : "sudo nautilus"

A NAUTILUS window will appear that has root priviledges, please navigate to your computer, plug the USB drive and take a look at it, see if it properly mounted and make sure that you can read /write there, then post back here the results.

Till then Cheers, TJ.

---

### Post by nrg762 on 2007-05-14
I use Kubuntu, not ubuntu. do i type "sudo Konqueror"?

---

