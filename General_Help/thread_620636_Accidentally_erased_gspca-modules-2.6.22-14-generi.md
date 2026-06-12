---
title: "Accidentally erased gspca-modules-2.6.22-14-generic"
date: 2007-11-22
forum: General Help
---

### Post by gastone_2005 on 2007-11-22
hello 

I accidentally erased gspca-modules-2.6.22-14-generic as the title says so I can;t install it via Synaptics..

I tried to run sudo apt-get install gspca-modules-2.6.22-14-generic but it returns that this package is not available but it has a reference in the database..something like that..

In the end I can't install it and I really need it..

Can I do anything besides going on liveCD an copy the file?

I looked up at Debian package archive but it was not there...

Thx for any answers / thoughts / solution..

---

### Post by bettlebrox on 2007-11-22
The only pacakge I can find (in gutsy) that's got anything to do with gspca is the  gspca-source package:
[http://packages.ubuntu.com/gutsy/graphics/gspca-source](http://packages.ubuntu.com/gutsy/graphics/gspca-source)

I think when you compile this it creates a .deb that you then install.

---

### Post by gastone_2005 on 2007-11-22
yes i saw that too..

But you see I don't want to compile again gspca..

That was my mistake before and so afterwards I erased by mistake these files..

What i want now is to install gspca-source and gspca-modules-2.6.22-14-generic from Synpatic, and hopefully see my camera working:)

By the way how do I remove a manually compiled module from my system?

---

### Post by loell on 2007-11-22
how did you accidentally remove/erased a module?

---

### Post by gastone_2005 on 2007-11-22
well lets see..

I wanted to get my camera working...This camera is supported by the gspca driver.Untiil now, I had no idea that gspca was available through Synaptics so I followed some online instructions and compiled it my self..

When I heard about gspca on Synaptics I intalled it via Synpatics too, but then i realized how stupid that was an wanted to uninstall the one that I  compiled manually, but didn't know how..

So I use Google, but can't find anything that helps..

And i freakout

I open a terminal,

sudo locate gspca

and started rm -rf all the directories locate returned :/

I know its stupid but I missed 48 hours of my life with gspca and so I knew sth had to be done..

Now..Do you know anything that can help?

Oh and btw I think i erased the package with that name, not the module.. ;)

---

### Post by loell on 2007-11-22
hmm, why did you compile gspca? it is already installed by default in gutsy. ;)

in any case, i think you can also find it on the cd, with directories

```

/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1
/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko
```

---

### Post by gastone_2005 on 2007-11-23
> **loell said:**
> hmm, why did you compile gspca? it is already installed by default in gutsy. ;)

in any case, i think you can also find it on the cd, with directories

```

/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1
/lib/modules/2.6.22-14-generic/ubuntu/media/gspcav1/gspca.ko
```

Well the webcam didn't work out-of-the-box as it should so I was desperate to find a way to make it work I guess..Unfortunately I didn't think of looking in Synpatics for gspca..

Anyway, thx loell, I' ll try it and send my feeback...:):)

---

### Post by gastone_2005 on 2007-11-24
I already had the above files in the same directories..

In the live CD I didn't find gspca-modules-2.6.22-14-generic package..I just got the same files in the same direcories as mentioned above..

What am I supposed to do..Should I reinstall Ubuntu..?

Or perhaps have somebody with the same kernel and same version (gutsy) send me the file?

---

### Post by gastone_2005 on 2007-11-24
ok i got it alla back like before, by aking the deb files of gspca-source and gspca-modules from the second installation that ubuntu has..

Now my problem is (and was before i guess) that when i connect the camera, there is no video0 file created..

Any ideas?

Edit: my webcam is a Toshiba PX1342E-1CAM Usb webcam\

The output of lsusb is:

Bus 001 Device 005: ID 093a:2608 Pixart Imaging, Inc.

which is similar to Trust wb-3300p and according to[ gspca driver page]("http://mxhaard.free.fr/spca5xx.html") should work out-of-the-box..but it doesn't..

---

### Post by loell on 2007-11-24
depends on what you really need. a question though,

can you find any link that your webcam is working under linux?

cause if its not known to work then reinstalling ubuntu wouldn't make a difference.

---

### Post by loell on 2007-11-24
> **gastone_2005 said:**
> ok i got it alla back like before, by aking the deb files of gspca-source and gspca-modules from the second installation that ubuntu has..

Now my problem is (and was before i guess) that when i connect the camera, there is no video0 file created..

Any ideas?

what's your webcam's device ID? 

try ```
lsusb
``` then copy/paste the output.

---

### Post by gastone_2005 on 2007-11-24
No I can't find any link that sais my camera works under linux :(

But as I said in my earlier post loell it has the same chip with a camera that is known to work with linux..

Isn't that enough or it doesn't matter?:confused:

Thx for your answers loell, I really appreciate it :)

Edit: Look previous post ;) i got the id there..

---

### Post by loell on 2007-11-24
its not just the same chipset, its actually the exact device as your webcam in the spca page ;)

Trust 	239 	0x093a 	0x2608 	WB 300P 	


so its just strange that i didn't work :(

perhaps the report was not accurate? i dunno. we'll gonna need other user of this cam to confirm this.

---

### Post by gastone_2005 on 2007-11-24
> **loell said:**
> its not just the same chipset, its actually the exact device as your webcam in the spca page ;)

Trust 	239 	0x093a 	0x2608 	WB 300P 	


so its just strange that i didn't work :(

perhaps the report was not accurate? i dunno. we'll gonna need other user of this cam to confirm this.

Yeah, I guess someone else will have to confirm if it does or doesn't work..

Anyone?

btw it's TRUST WB-3300P not WB-300P..it's misspelled  in that page..

---

