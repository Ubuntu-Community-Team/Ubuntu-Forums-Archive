---
title: "A couple questions about Compiz"
date: 2008-05-05
forum: General Help
---

### Post by jamieh on 2008-05-05
I saw [this video]("http://ca.youtube.com/watch?v=-lcv_l7Y73o") on YouTube, and I have a couple questions:

1) How do you get those moving gears in the middle of the cube?
2) How do you change the background of the cube area? (Like he has that scene of buildings)

Thanks!

---

### Post by agim on 2008-05-05
sudo apt-get install ccsm

after the install

System->Preferences->Advanced Desktop Effects

---

### Post by tw3k on 2008-05-05
> **jamieh said:**
> I saw [this video]("http://ca.youtube.com/watch?v=-lcv_l7Y73o") on YouTube, and I have a couple questions:

1) How do you get those moving gears in the middle of the cube?
2) How do you change the background of the cube area? (Like he has that scene of buildings)

Thanks!

I think it varies on which desktop environment you use. For me, I use gnome, the Advanced Desktop Effects in the Gnome Control Center are the compiz settings.

You'll see Cube Gears in the Effects section and image in the Desktop Cube -> Appearance tab.

---

### Post by tommyhakinen on 2008-05-06
> **jamieh said:**
> I saw [this video]("http://ca.youtube.com/watch?v=-lcv_l7Y73o") on YouTube, and I have a couple questions:

1) How do you get those moving gears in the middle of the cube?
2) How do you change the background of the cube area? (Like he has that scene of buildings)

Thanks!

Okay, I assume you are using Ubuntu. First, you need to install compizconfig-settings-manager.

> sudo apt-get install compizconfig-settings-manager

after installation, go to

> System > Preferences > Advanced Desktop Effects Settings

Enable all these:
Desktop Cube, Rotate Cube, Cube Reflection, Cube Gears

To have Background when you are rotating the Cube, go to Desktop Cube > Appearance Tab. Look for "Skydome" and add the image you want it to be the background.

To have the gears in the middle of the cube, you need to set the cube to be transparent. Still on the Desktop Cube, go to Transparent Cube, and adjust the Opacity.

Now when you are rotating the cube, you will be able to see the Gears in the center of the Cube.

Good luck.

Regards,

tommy

---

### Post by jamieh on 2008-05-06
Yes, I'm using Ubuntu 8.04.
Thanks for all your help!

---

