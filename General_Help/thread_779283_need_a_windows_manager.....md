---
title: "need a windows manager....?"
date: 2008-05-02
forum: General Help
---

### Post by 565Customz on 2008-05-02
compiz is telling me a need a windows manager, and it wont enable the cube or other functions. anyone know what i should do?

thanks

---

### Post by scottuss on 2008-05-02
Compiz is a Window Manager. Did you mean Window Decorator? Search in Synaptic (System > Administration > Synaptic Package Manager) for Emerald, and install that.

If it wont allow advanced desktop effects, it may be that your graphics drivers are not compatible. Are you using the restricted drivers?

Check under Administration > Hardware Drivers

---

### Post by 565Customz on 2008-05-02
now it tells me, when i click on preferences> appearence  that it cant change desktop settings...? wtf

---

### Post by scottuss on 2008-05-02
OK so did you check if you're using restricted drivers? If not, you need to be.

A good tool to select both your window manager and window decorator is the Compiz-Fusion icon program.

Install fusion-icon from synaptic, then launch it. Right click on it's icon and under "Select Window Manager" select compiz

then under "Select Window Decorator" select emerald.

Remember you need the restricted drivers installed and enabled first!

---

### Post by 565Customz on 2008-05-02
sorry man i didnt even see your first post, you must have been posting at the same time i was. i had them installed when i  had gutsy, but when i upgraded i must have forgot to reinstall them.  im not sure how to allow them, can you tell me

---

### Post by 565Customz on 2008-05-02
got this when installing fusion icon

E: fusion-icon: subprocess post-installation script returned error exit status 1

is that because of the drivers

---

### Post by scottuss on 2008-05-02
I don't think so. To enable the restricted drivers click System > Administration > Hardware Drivers

When that loads up you should see an entry for the ATI restricted drivers on there. It will probably say "not in use" so if you tick the box on there the light will turn green and will say "in use"

Once thats done, reboot and check that they are still "in use"

That means that your drivers are now working if so. 

Then check the following:
[LIST]
[*]Compiz is installed
[*]Emerald is installed
[*]Advanced Desktop Effect Settings Is installed
[/LIST]

If you can say yes to all of the above, try the Compiz-Icon thing again. If it doesn't work, I'm stumped! :confused:

---

### Post by 565Customz on 2008-05-02
the only thing that is listed under the drivers is my wireless  card...thats it. it has no options for restricted drivers, or video drivers....? i have full athourity under this user

---

### Post by scottuss on 2008-05-02
OK. Under Synaptic do a search for "fglrx" and install the xorg-driver-fglrx. 

This should fix the issue of not having the restricted drivers. If that doesn't work I really am stuck! Sorry that I can't be more help :(

---

### Post by 565Customz on 2008-05-02
tryin it now

---

### Post by 565Customz on 2008-05-02
i think that is for ati stuff and i dont have and ati.... also i dont see the xorg..... under synaptic

---

### Post by 565Customz on 2008-05-02
actually i see it now, just missed it. but i still think that is for ati stuf
f

---

### Post by scottuss on 2008-05-03
Oh sorry man, for some reason I thought you were using ATI. What graphics chip you got? Is it Nvidia or perhaps Intel?

If it's Nvidia, there are restricted drivers for that. For Intel ones Im not so sure...

---

