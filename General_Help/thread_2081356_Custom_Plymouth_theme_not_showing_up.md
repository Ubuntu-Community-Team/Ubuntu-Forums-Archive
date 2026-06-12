---
title: "Custom Plymouth theme not showing up"
date: 2012-11-06
forum: General Help
---

### Post by Ru1138 on 2012-11-06
I've created a custom Plymouth theme for Ubuntu 12.10. The problem is that when I run the X11 plugin (the one that lets me see the splash without rebooting) it shows a black screen. I tried the FRAMEBUFFER=y technique but that didn't do anything. I'm completely stuck.

---

### Post by Ru1138 on 2012-11-07
Bump and new information. Here's my current .plymouth file:

```
[Plymouth Theme]
Name=Cornflower
Description=Cornflower plymouth theme
ModuleName=script

[script]
ImageDir=/lib/plymouth/themes/cornflower/Untitled.png
ScriptFile=/lib/plymouth/themes/cornflower/cornflower.script
```

And here's my current .script file:

```
flower_image = Image(Untitled.png);
flower_sprite = Sprite(flower_image);
flower_sprite.SetX(Window.GetWidth()/2 - flower_image.GetWidth()/2);
flower_sprite.SetY(Window.GetHeight()/2 - flower_image.GetHeight()/2);
progress = 0;
fun refresh_callback ()
  {
   progress++;
   flower_sprite.Rotate(progress);
  }
Plymouth.SetRefreshFunction (refresh_callback);
```

---

### Post by Ru1138 on 2012-11-08
A friend of mine made a new .script file.

```
screen_width = Window.GetWidth ();
screen_height = WIndow.GetHeight ();

counter = 25;

flower = Image ("Untitled.png");
sprite_flower = Sprite (flower);

fun refreshHandler () {

sprite_flower.SetPosition ((screen_width / 2) - (flower.GetWidth () / 2), (screen_height / 2) - (flower.GetHeight () / 2));
sprite_flower.SetImage(flower.Rotate(counter));

counter++;

}

Plymouth.SetRefreshFunction (refreshHandler);
```

In addition, I appended the  --debug command to sudo plymouthd and the command line stops at "entering main event loop" and I don't get a line to enter further commands. Plus, I've checked other themes (albeit without --debug appended) and they work fine. I'm completely stumped. :(

---

