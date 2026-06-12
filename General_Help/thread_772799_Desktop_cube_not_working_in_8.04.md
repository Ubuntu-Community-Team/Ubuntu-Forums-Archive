---
title: "Desktop cube not working in 8.04"
date: 2008-04-28
forum: General Help
---

### Post by WildeBeest on 2008-04-28
I just installed Hardy in a new partition over the weekend.

I have a nvidia  8500gs graphics card.
Hardware Drivers lists the nvidia driver(latest cards).

I can't get the desktop cube working.
I have everything setup correctly, I believe. At least how I had things set in 7.10.

Any help would be appreciated.

---

### Post by alsamman on 2008-04-28
> **WildeBeest said:**
> I just installed Hardy in a new partition over the weekend.

I have a nvidia  8500gs graphics card.
Hardware Drivers lists the nvidia driver(latest cards).

I can't get the desktop cube working.
I have everything setup correctly, I believe. At least how I had things set in 7.10.

Any help would be appreciated.

are any of the other effects working? (I assume you are using Compiz)

---

### Post by WildeBeest on 2008-04-28
Yes, I am using compiz.

I believe other effects are working.

---

### Post by sowelie on 2008-04-28
Did you install the compizconfig-settings-manager?  I don't think the rotate cube plugin is enabled by default.

---

### Post by WildeBeest on 2008-04-28
> **sowelie said:**
> Did you install the compizconfig-settings-manager?  I don't think the rotate cube plugin is enabled by default.

Installed and cube plug-in is enabled.

Like I posted earlier. I have it working on my 7.10 install.

---

### Post by sowelie on 2008-04-28
So when you push CTRL+ALT+Click and drag the cube doesn't rotate, are you sure the "Rotate Cube" plugin is enabled and that the keys have been bound properly?

Also, ensure that compiz is actually running, try typing compiz --repalce in the console and see what output you get.

---

### Post by WildeBeest on 2008-04-28
> **sowelie said:**
> So when you push CTRL+ALT+Click and drag the cube doesn't rotate, are you sure the "Rotate Cube" plugin is enabled and that the keys have been bound properly?

Also, ensure that compiz is actually running, try typing compiz --repalce in the console and see what output you get.

Thanks, turns out I didn't have the rotate plugin eneabled.

Thanks.

---

### Post by Azrael Strife on 2008-04-28
I have a question regarding this.
My "cube" is only bidimensional, when I try to rotate it, my screen just flips, it's a plane, not a cube, this seems to be due to the fact I have only two possible desktops (Ubuntu 8.04), is there a way to have four and use the cube?

---

### Post by Zorael on 2008-04-28
> **Azrael Strife said:**
> I have a question regarding this.
My "cube" is only bidimensional, when I try to rotate it, my screen just flips, it's a plane, not a cube, this seems to be due to the fact I have only two possible desktops Ubuntu 8.04), is there a way to have four and use the cube?

Go into General Options in ccsm (compizconfig-settings-manager), then to Desktop Size tab and set Horizontal Virtual Size to 4. Vertical Size and Number of Desktops should both be set to 1.

Of course, if you want a raised triangle, set horizontal to 3. Pentagonal 5, hexagonal 6, ad nauseum.

---

### Post by Azrael Strife on 2008-04-28
Thanks :)

---

### Post by ravenus on 2008-04-30
Problem solved. Sorry for haste :)

---

### Post by gqstatus05 on 2008-11-24
OMG. I was trying to figure out why my screen flipped. Thank you so much I would have never figured it out. Wow. I love Ubuntu, F*** Windows.

---

### Post by blueflyt on 2008-11-25
Mr. Noob here...

Can someone kindly tell me how to configure compiz?  I'm running 8.10 and I see all kinds of threads on compiz, but I don't see it as a menue option.  Is it a package I have to install or what?  

Thanks.

---

### Post by blueflyt on 2008-11-25
Ok, I went into the Synaptics package manager and loaded the compiz configuration package.  From what I can tell, I've got everything properly configured to run the Cube affect.  Still a no-go.  Any help is appreciated.

---

