---
title: "Custom Boot/Login Sound help ?"
date: 2021-08-11
forum: General Help
---

### Post by pascalsystem on 2021-08-11
Hey I'm running Ubuntu version 21.04, and I want to add a custom sound to either boot or login. I have tried both the [COLOR=#242729][FONT=ui-monospace]paplay[/FONT][/COLOR] and [COLOR=#242729][FONT=ui-monospace]canberra-gtk-[/FONT][/COLOR]  methods as suggested on other websites. Neither of these seem to work. Does anybody know a surefire way to do this?

---

### Post by mIk3_08 on 2021-08-11
Most Ubuntu uses GNOME Login Sound and it works great and perfectly suites to my Ubuntu System. And I haven't heard surefire.
If you are about to setup GNOME Login Sound just search the "Startup Applications" and just add the Field below:

```
Field: Name: GNOME Login Sound
Field: Command:  /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Field: Comment: Plays a sound whenever you log in
```
or Field: Command
```
Field: Command: paplay /usr/share/sounds/Location/of/your/Ubuntu/stereo/desktop-login.ogg
```
Then Save and you are done! That's it. Good Luck and Regards.

---

### Post by calarndt on 2021-08-11
Just curious
Does this file exist on your system?
/usr/share/sounds/Yaru/stereo/system-ready.oga

if it does? What happens when you:
canberra-gtk-play /usr/share/sounds/Yaru/stereo/system-ready.oga

mine gets an error msg:

root@carndt-Z170XP-SLI:/home/carndt# canberra-gtk-play /usr/share/sounds/Yaru/stereo/system-ready.oga
Unable to init server: Could not connect: Connection refused
Option parsing failed: Cannot open display:

---

### Post by mIk3_08 on 2021-08-12
> **calarndt said:**
> Just curious
Does this file exist on your system?
/usr/share/sounds/Yaru/stereo/system-ready.oga

if it does? What happens when you:
canberra-gtk-play /usr/share/sounds/Yaru/stereo/system-ready.oga

mine gets an error msg:

root@carndt-Z170XP-SLI:/home/carndt# canberra-gtk-play /usr/share/sounds/Yaru/stereo/system-ready.oga
Unable to init server: Could not connect: Connection refused
Option parsing failed: Cannot open display:

I don't have any .oga format in my system, maybe you should convert that one to .ogg audio format. 
And I haven't encountered this .oga audio format yet. 
I think you should install sox in your system. so you can play music using your terminal

```
sudo apt-get install sox
```
Then this dependencies:
```
Dayun kani
sudo apt-get install sox libsox-ft-all
```
```
sudo apt-get install sox libsox-fmt-all
```
and the command in playing music using terminal;
```
paplay '/home/Music/Location/Ubuntu/music/folder/stereo/login.ogg'
```

---

### Post by pascalsystem on 2021-08-12
Thank you so much for posting! I did that and boom, startup sound is working with the paplay command :3

---

### Post by mIk3_08 on 2021-08-13
> **pascalsystem said:**
> Thank you so much for posting! I did that and boom, startup sound is working with the paplay command :3
Maybe if you have some time you can mark this thread as solve so that you can help some new ubuntuforum users that has same problem with this thread might see this as a solution solve.
Marking this thread as solve helps to other new user in this community see in search as a working solution solve issues.
Just click link below under my signature Solve thread for more information to mark this thread as solve. Thanks a lot and Good Luck. Enjoy!

---

