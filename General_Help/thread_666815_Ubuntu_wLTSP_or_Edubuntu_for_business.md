---
title: "Ubuntu w/LTSP or Edubuntu for business ?"
date: 2008-01-13
forum: General Help
---

### Post by fredsnet on 2008-01-13
Is it better to install Ubuntu server and then add LTSP for a business Not educational application.  Or is it better to install Edubuntu and remove the educational applications ?

I currently work for a company that is interested in breaking away from windows handcuffs.

To educate myself and learn the ins and outs of a thin client system, I want to set up a system in my home to educate myself in how to setup and manage a LTSP server.  I already have a windows network and have started by installing ubuntu desktop on my notebook. A trip to the office to let everybody see it really peaked the interest level.

So is it Edubuntu or Ubuntu w/LTSP.   Most likely will not need to use the server for anything else but internet access for the thin clients.

thanks,

Fred

---

### Post by Dragonbite on 2008-01-14
I find Edubuntu pretty easy to set up and other than the Gartoons and the wallpaper it isn't inundated with kids games in 7.10. Plus you can easily remove them in Synaptic or Add/Remove programs.

It comes with OpenOffice, but like any Linux systems you can pretty much add what you want and remove what you don't want.  My big issue was getting LTSP working in the first place (which I have).

I think I also installed **ubuntu_artwork** and got the Ubuntu generic wallpaper and the Human theme was already installed os for my screen it looks like Ubuntu (while my kids still get Edubuntu).

---

### Post by fredsnet on 2008-01-14
Thanks so much for your response.  

 I am seeing a lot of request for a dedicated forum on LTSP, I think that is a good idea. I couldn't even decide where to post this topic.  I also think that a "Ubuntu in Business" would also be a good forum.  I am sure there are many considering the possibilities and savings of setting up LTSP systems in their work environments. 

I orignally was working with Sun Solaris 10 and considering a Sun Ray thin client system. But, after hours and hours of problems with the base software. I went looking for a better alternative to thin client systems.  This search led me to Ubuntu and I am really impressed.
 
This OS is so much more refined and end user friendly than Solaris.  I think Sun has a good large system OS but it is way to problematic for a SOHO or medium size company or school to consider using it.  I will say that Sun's Java updates to my XP desktop is what started my curiosity.  Attached to the update was a advertisement to try Open Office.Org Suite. Impressed I started to consider how far I could stray from Windows.  I have jumped out the window and running as fast as I can.

Thanks again,

Fred

---

### Post by maybeway36 on 2008-01-18
Install regular Ubuntu and add the edubuntu-server (NOT the edubuntu-desktop). Works just fine.

---

### Post by Dragonbite on 2008-01-18
I read somewhere that Edubuntu is supposed to have made some things to help run KDE through the Thin clients.  

Be interested in what kind of performance hit it takes, but that could open up some options especially in the business sector if you are migrating from Windows.

I have already installed Xfce (not Xubuntu, just Xfce) and it's handy to have that option, but I'm trying to figure out how to have my thin client startup with Xfce, but when I'm loging into the server itself it gives me Gnome (which has more system-tools easily visible).

---

### Post by maybeway36 on 2008-01-18
I installed kubuntu-desktop and edubuntu-server once, and it worked pretty much perfectly over LTSP. The only thing was that the LTSP fuse devices (local CD, disks on the thin client) did not appear on the desktop, and you had to go to /media. Otherwise, quite nice.

---

