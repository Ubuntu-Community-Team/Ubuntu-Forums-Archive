---
title: "Pakage installation without net connection !"
date: 2007-10-25
forum: General Help
---

### Post by suj2007 on 2007-10-25
One of my friend requested me to install Ubuntu gutsy in his PC. But he have no Net connection. I installed the same in his computer. Now I want to install some other pakages which are not installed by default. I wish to copy these pakages in CD/DVD and wish to install in his PC. 
Now I dont know in my PC in  which folder the pakeges are stored that I can copy to CD.

I shall be glad if any one tell me the exact location of these pakages in the PC.
thanks

---

### Post by Maestro23 on 2007-10-25
Check the following procedure out using the "Generate Package Download Script" function in Synaptic.  Should help with what you want to do.

[http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/](http://beans.seartipy.com/2006/11/03/simple-way-to-update-ubuntu-edgy-with-slowno-internet-connection/)

Good luck man. :guitar:

---

### Post by mahousaru on 2007-10-25
I don't think Ubuntu keeps the installation files after installing...  But for your problem I personally would grab the debs from

[http://www.getdeb.net/](http://www.getdeb.net/)

Or if you want to overkill

[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

*EDIT*

@Maestro23 - Nice link!

---

### Post by Maestro23 on 2007-10-25
> **mahousaru said:**
> I don't think Ubuntu keeps the installation files after installing...  But for your problem I personally would grab the debs from

[http://www.getdeb.net/](http://www.getdeb.net/)

Or if you want to overkill

[http://www.howtoforge.com/dvd_images_of_ubuntu_repositories](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories)

*EDIT*

@Maestro23 - Nice link!

Thanks man.  I found that some time ago, and tried it out on a friend's laptop a few days ago.  Downloaded the packages using my broadband connection, went over to his house and installed everything without a hitch.  I was impressed. :)

---

### Post by suj2007 on 2007-10-26
> **mahousaru said:**
> I don't think Ubuntu keeps the installation files after installing...  But for your problem I personally would grab the debs from
!

I think  packages  download/updated through syneptic package manager is kept in some folder. I thinks so because if we uninstall some programme for any reason and again decided to install the same, in that case we can install the programme with out connecting the net.

---

### Post by suj2007 on 2007-10-27
I dont  get any suitable answer from this forums. However I got the answer the packages installed by the syneptic/adept package manager are stored in

/var/cache/apt/archives

---

