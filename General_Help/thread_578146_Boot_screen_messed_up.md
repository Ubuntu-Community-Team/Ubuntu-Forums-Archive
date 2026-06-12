---
title: "Boot screen messed up"
date: 2007-10-16
forum: General Help
---

### Post by Linux_noob1 on 2007-10-16
I had just installed ubuntu-desktop and xubuntu-desktop on my Kubuntu system.


Things are well except that I cannot get my Kubuntu boot screen back. Instead I had gotten the Ubuntu one.

I tried

 sudo update-alternatives --config usplash-artwork.so

selected the right number for Kubuntu,

then typed

sudo dpkg-reconfigure linux-image-`uname -r`


Now im getting the Xubuntu boot screen. I tried it again and got the same results.

This isn't a severe problem but its still a little irritating since it seems I just can't get the Kubuntu boot screen back.
Any suggestions?

Thanks.

---

### Post by zvacet on 2007-10-17
Did you try in login window in bottom left corner under sessions select Kubuntu?This can be helpfull too

[http://www.psychocats.net/ubuntu/purekde]("http://www.psychocats.net/ubuntu/purekde")

---

### Post by Linux_noob1 on 2007-10-17
> Did you try in login window in bottom left corner under sessions select Kubuntu?This can be helpfull too

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

Im confused, there is only a shutdown and restart button on the bottom left in the Xubuntu boot menu?

Should I just go back too

*sudo update-alternatives --config usplash-artwork.so*

 and hit different numbers until I get Kubuntu screen back? The values seemed to a little off.


Thanks for the help,

---

### Post by Linux_noob1 on 2007-10-17
Ok I just selected Xubuntu with

sudo update-alternatives --config usplash-artwork.so

and then instead of me getting the Kubuntu loading screen and the Xubuntu login screen, I got the Xubuntu loading screen and the Xubuntu login screen.

So I went back too

sudo update-alternatives --config usplash-artwork.so
 
and set it to Kubuntu. Now im getting the Kubuntu loading screen, but I am still getting the Xubuntu login screen.

How can I get my old Kubuntu login screen back?

---

### Post by por100pre1 on 2007-10-17
```
sudo dpkg-reconfigure kdm
```

and then select KDM.

---

### Post by Linux_noob1 on 2007-10-17
> 
Code:

sudo dpkg-reconfigure kdm

and then select KDM.


It worked, thanks!


Thanks for the help everyone!

---

