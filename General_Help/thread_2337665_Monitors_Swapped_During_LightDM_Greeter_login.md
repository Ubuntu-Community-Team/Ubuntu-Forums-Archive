---
title: "Monitors Swapped During LightDM Greeter login"
date: 2016-09-20
forum: General Help
---

### Post by Jumbs on 2016-09-20
I recently replaced my super old video card with something more current.

Everything went smoothly, except i cannot get the greater in LightDM to correctly span the monitors.  Exiting my mouse on the right of the right monitor enters the left of my left monitor.
Once logged in, my settings take over, and it swaps correctly. 

I have tried a lot of options on the web, but none have worked.

[B]I have copied ~/.config/monitors.xml to /var/lib/lightdm/.config to no success.

I have added ```
xrandr --output DVI-D-0 --right-of HDMI-0 
``` to display-setup-script, greeter-setup-script, session-setup-script in /etc/lightdm/lightdm.conf
[/B]
Sometimes the settings look like they take, with the mouse spanning correctly, or the nvidia logo being centered during boot, but always by the time the greeter appears, they are on the wrong side.

And no, swapping the cables wont work!

Thanks!

---

### Post by DuckHook on 2016-09-20
> **Jumbs said:**
> And no, swapping the cables wont work!You are correct. Simply swapping cables won't work. Swapping *monitors* would, but cables, no. This is because the system goes through a monitor ID process at boot to determine relative placement and ignores port and cable. This is proper behaviour. After all, cables can get switched frequently, especially if it's a laptop that gets plugged and unplugged all the time, whereas monitors are more permanent.
> I have copied ~/.config/monitors.xml to /var/lib/lightdm/.config to no success.Not surprising. Writing to the /var/lib/lightdm directory is not as simple as invoking *sudo*. This is because the /var/lib/lightdm directory is not actually owned by root but by lightdm. lightdm is a special user, and if you look at this directory's permissioning, it is:```
rwxr-x---
```&#8230;or 750 in Octal. This means that no "others" can access it in any way. Since root is considered an "other", even sudo cannot make changes to the directory without first being allowed access. The easiest way to do this is to first:```
sudo chmod 777 /var/lib/lightdm
```&#8230;then:```
sudo cp /home/your_user_name/.config/monitors.xml /var/lib/lightdm/
```&#8230;replacing your_user_name and being sure to include the trailing slash "/". Also, make sure that the monitors.xml file exists and reflects what you want displayed. Then change ownership of resulting file with:```
sudo chown lightdm:lightdm /var/lib/lightdm/monitors.xml
```&#8230;and finally, set directory back to original permissions with:```
sudo chmod 750 /var/lib/lightdm
```Tell us how it goes.

---

### Post by Jumbs on 2016-09-20
Sorry, I was a little loose with my explanation. I am fully versed in linux and the command line.

-I was able to move the monitors.xml file, but it did not change the result. I also tried adjusting the permissions without any luck. 

As for the cables, one is HDMI, the other is DVI, so swapping the cables wont work without some adapters. 

I was able to get it to work by changing the DM to GDM3.  That, plus moving the monitors.xml file to the correct GDM folder made it work during login.

I would prefer to switch back to lightdm if possible though, so keep the suggestions coming!

---

### Post by DuckHook on 2016-09-20
In that case, you followed the process that I've always used in the past and the only one I know. systemd has done many strange things to configurations that I am still learning. Perhaps other users can fill us both in.

---

### Post by Jumbs on 2016-09-20
For now, ill just use GDM, even with its annoying lock screen

---

