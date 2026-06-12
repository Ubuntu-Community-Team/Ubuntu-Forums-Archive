---
title: "ubuntu running painfully slow.."
date: 2013-09-12
forum: General Help
---

### Post by ben19 on 2013-09-12
hello everyone i have tryed just about every distro out there no idea why they all go slow and freeze i have an amd fx 6300 cpu with a radeon hd 6770 and an asrock motherboard with 8 gigs of kingston ram and a regular 500gig hd no problems with windows 7 im just getting bored with it and want to use something different i have used this in the past with an intel cpu and nvidia card and i had no such issues .. any tips i could try to make this work better? , oh i also get a black screen after install and i have to add nomodeset to the boot menu.

---

### Post by QIII on 2013-09-12
Hello!

Would you please install htop

```
sudo apt-get htop
```

and then run it in the terminal

```
htop
```

when you feel it is running slowly?

Press CNTL+C when it is running to stop the updates, highlight all the text in the terminal and press CNTL+SHIFT+C to copy it and paste the results back here?

We can take a look at that and see if there is something hogging your resources.

---

### Post by HiImTye on 2013-09-12
if you're using regular Ubuntu, then make sure you're using the proprietary drivers (Software Sources > Additional Drivers), otherwise you're using llvmpipe which is painfully inefficient.

---

### Post by ben19 on 2013-09-12
hello guy's thanks for the replies it runs slow even after the amd driver install.. im going to re install and post those results .

---

### Post by lilcrazyjjjs on 2013-09-12
i disabled cool and quiet in my bios and things are launchin quick ...do i need that setting ? im not sure

---

### Post by HiImTye on 2013-09-13
you can always try a different DE, I'm pretty partial to Lubuntu, but there's other DEs
```
sudo apt-get install lubuntu-desktop
sudo apt-get install gnome-desktop-environment
sudo apt-get install kubuntu-desktop
sudo apt-get install xubuntu-desktop
```
or there's a multitude of others available. here's a link to some of the main ones [http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available](http://askubuntu.com/questions/65083/what-different-desktop-environments-and-shells-are-available)

---

### Post by Mephisto Pheles on 2013-09-13
With 8 gigs of RAM you should be able to run unity, that is the standard ubuntu DE.

---

