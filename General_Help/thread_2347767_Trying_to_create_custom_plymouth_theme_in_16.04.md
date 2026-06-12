---
title: "Trying to create custom plymouth theme in 16.04"
date: 2016-12-28
forum: General Help
---

### Post by el_Paraguayo on 2016-12-28
I'm having trouble trying to create a custom plymouth theme in 16.04.

I have a folder called /usr/share/plymouth/themes/my-htpc which contains a logo.png file plus the relevant .plymouth and .script files (see below).

my-htpc.plymouth
```
[Plymouth Theme]Name=HTPC Splash Theme
Description=A theme that features a blank background with a logo.
ModuleName=my-htpc


[my-htpc]
ImageDir=/usr/share/plymouth/themes/my-htpc
ScriptFile=/usr/share/plymouth/themes/my-htpc/my-htpc.script

```
my-htpc.script
```
wallpaper_image = Image(“logo.png”);
wallpaper_sprite = Sprite(wallpaper_image);
wallpaper_sprite.SetZ(-100);

```
I've then tried
```
sudo update-alternatives --install /usr/share/plymouth/themes/default.plymouth default.plymouth /usr/share/plymouth/themes/my-htpc/my-htpc.plymouth 100
```
and then
```
[COLOR=#110000]plymouthd; plymouth [/COLOR][COLOR=#660033][FONT=inherit]--show-splash[/FONT][/COLOR][COLOR=#110000] ; [/COLOR][COLOR=#000000][FONT=inherit]**for**[/FONT][/COLOR][COLOR=#7A0874][FONT=inherit]**(**[/FONT][/COLOR][COLOR=#7A0874][FONT=inherit]**(**[/FONT][/COLOR][COLOR=#007800][FONT=inherit]I[/FONT][/COLOR][COLOR=#110000]=[/COLOR][COLOR=#000000][FONT=inherit]0[/FONT][/COLOR][COLOR=#110000]; I[/COLOR][COLOR=#000000][FONT=inherit]**<**[/FONT][/COLOR][COLOR=#007800][FONT=inherit]5[/FONT][/COLOR][COLOR=#110000]; I++[/COLOR][COLOR=#7A0874][FONT=inherit]**)**[/FONT][/COLOR][COLOR=#7A0874][FONT=inherit]**)**[/FONT][/COLOR][COLOR=#110000]; [/COLOR][COLOR=#000000][FONT=inherit]**do**[/FONT][/COLOR][COLOR=#110000] plymouth [/COLOR][COLOR=#660033][FONT=inherit]--update[/FONT][/COLOR][COLOR=#110000]=[/COLOR][COLOR=#7A0874][FONT=inherit]**test**[/FONT][/COLOR][COLOR=#007800][FONT=inherit]$I[/FONT][/COLOR][COLOR=#110000] ; [/COLOR][COLOR=#C20CB9][FONT=inherit]**sleep**[/FONT][/COLOR][COLOR=#000000][FONT=inherit]1[/FONT][/COLOR][COLOR=#110000]; [/COLOR][COLOR=#000000][FONT=inherit]**done**[/FONT][/COLOR][COLOR=#110000]; plymouth quit[/COLOR]
```but I get a grey screen with text saying 16.04.

Running update-initramfs makes no difference (and my understanding is that it's not necessary when previewing themes).

Does anyone have any ideas?

---

### Post by el_Paraguayo on 2016-12-29
I must be missing something. I tried by copying the ubuntu-logo theme and just renaming the filenames and got the same grey text screen.

---

### Post by el_Paraguayo on 2016-12-29
OK - looks like changing the "ModuleName" in the .plymouth file was the problem. Seems to be working now.

---

