---
title: "Impish launcher icon response lag"
date: 2021-12-07
forum: General Help
---

### Post by Paulgirardin on 2021-12-07
Hi

I have just fresh installed Impish and have seen a change in the behaviour of the launcher/dock.

When an app is launched , the icon takes 20 seconds to appear in the dock and ,likewise, when it is closed it takes 20 seconds to disappear.
The actual opening of the apps is not affected. They open and close virtually instantaneously.
While the icon remains in the dock for 20 secs after closing , it appears that the icon can be used to re-open the app.

I use Dash to Dock from extensions.gnome.org  but the behaviour is the same with the native version of the Dash to Dock that ships with Ubuntu.

My mode of use is to have no apps set as favourites in the dock , to open and close apps via keyboard actions and to use the dock to navigate open apps.

This 20 second lag appears like it may be intentional behaviour . I find it annoying as it affects my normal usage pattern.

Is this normal in Gnome 40 ?

---

### Post by Dennis N on 2021-12-07
Using the dash-to-dock extension in Ubuntu 21.10, upon launching a non-favorite application, I am seeing about 1-2 seconds for the icon to appear in the dock - basically equal to the time for the application itself to open. On closing, the icon vanishes almost instantly. So your experience is probably not normal.

---

### Post by Paulgirardin on 2021-12-07
Interesting. 
I've tried turning off the relevant extensions .
I might try uninstalling them.

That didn't help.
Not sure what is causing this.

---

### Post by Paulgirardin on 2021-12-07
It gets stranger.
I tried Dash to Panel and the delay happens with that too.
It seems to be a Gnome Shell problem and not just isolated to a specific extension

---

### Post by Dennis N on 2021-12-08
> **Paulgirardin said:**
> It gets stranger.
I tried Dash to Panel and the delay happens with that too.
It seems to be a Gnome Shell problem and not just isolated to a specific extension
You could be right. You could use Plank as a dock at least as a test of your suspicions since it is **not** a gnome-shell extension. It's appearance is very configurable. I use Plank as an alternative in all virtual machines, since Dash to Dock doesn't behave normally in them (if you set it to autohide, Dash to Dock won't appear on mouse pressure as in a regular install). One caveat is that Plank only works with Xorg, not Wayland. 

The default Ubuntu Dock? I just don't like its full height appearance.

Image: Plank dock in Ubuntu 21.10 virtual machine.

---

### Post by Paulgirardin on 2021-12-08
> **Dennis N said:**
> You could be right. You could use Plank as a dock at least as a test of your suspicions since it is **not** a gnome-shell extension. It's appearance is very configurable. I use Plank as an alternative in all virtual machines, since Dash to Dock doesn't behave normally in them (if you set it to autohide, Dash to Dock won't appear on mouse pressure as in a regular install). One caveat is that Plank only works with Xorg, not Wayland. 

The default Ubuntu Dock? I just don't like its full height appearance.

Image: Plank dock in Ubuntu 21.10 virtual machine.

Yes I might try that .

I don't like many things about the default Ubuntu Dock ,which is why I always install the extension developer's unmodified version of Dash to Dock.

---

### Post by Dennis N on 2021-12-08
> **Paulgirardin said:**
> Yes I might try that . I don't like many things about the default Ubuntu Dock ,which is why I always install the extension developer's unmodified version of Dash to Dock.

If you do try Plank, how to change the appearance is not that obvious at first glance.  

Ctrl+Rt Click on the dock brings up a menu where you find Preferences.  The themes offered there are very limited. The one in the screenshot uses a downloaded theme from gnome-look.org called [**Azeny**]("https://www.gnome-look.org/p/1463576/"). There are many others there under the category **Plank themes**.

A downloaded theme folder goes into **~/.local/share/plank/themes**

You customize the appearance with the **dock.theme** file that is within the theme folder which looks like this:

```
[PlankTheme]
TopRoundness=6
BottomRoundness=0
LineWidth=0
OuterStrokeColor=42;;50;;56;;164
FillStartColor=8;;31;;82;;164
FillEndColor=65;;97;;158;;164
InnerStrokeColor=42;;50;;56;;0


[PlankDockTheme]
HorizPadding=1.4
TopPadding=2
BottomPadding=1.6

ItemPadding=4
IndicatorSize=15
IconShadowSize=1

UrgentBounceHeight=1.6
LaunchBounceHeight=0.625
FadeOpacity=1
ClickTime=300
UrgentBounceTime=600
LaunchBounceTime=600
ActiveTime=300
SlideTime=300
FadeTime=250
HideTime=250
GlowSize=30
GlowTime=10000
GlowPulseTime=2000
UrgentHueShift=150
ItemMoveTime=450
CascadeHide=true
BadgeColor=0;;0;;0;;0

```
This one has a blue color. I made variations and saved them in a custom-named folders (for example, Azeny-Blue).

---

### Post by Paulgirardin on 2021-12-09
> **Dennis N said:**
> If you do try Plank, how to change the appearance is not that obvious at first glance.  

Ctrl+Rt Click on the dock brings up a menu where you find Preferences.  The themes offered there are very limited. The one in the screenshot uses a downloaded theme from gnome-look.org called [**Azeny**]("https://www.gnome-look.org/p/1463576/"). There are many others there under the category **Plank themes**.

A downloaded theme folder goes into **~/.local/share/plank/themes**

You customize the appearance with the **dock.theme** file that is within the theme folder which looks like this:

```
[PlankTheme]
TopRoundness=6
BottomRoundness=0
LineWidth=0
OuterStrokeColor=42;;50;;56;;164
FillStartColor=8;;31;;82;;164
FillEndColor=65;;97;;158;;164
InnerStrokeColor=42;;50;;56;;0


[PlankDockTheme]
HorizPadding=1.4
TopPadding=2
BottomPadding=1.6

ItemPadding=4
IndicatorSize=15
IconShadowSize=1

UrgentBounceHeight=1.6
LaunchBounceHeight=0.625
FadeOpacity=1
ClickTime=300
UrgentBounceTime=600
LaunchBounceTime=600
ActiveTime=300
SlideTime=300
FadeTime=250
HideTime=250
GlowSize=30
GlowTime=10000
GlowPulseTime=2000
UrgentHueShift=150
ItemMoveTime=450
CascadeHide=true
BadgeColor=0;;0;;0;;0

```
This one has a blue color. I made variations and saved them in a custom-named folders (for example, Azeny-Blue).

Thanks for the info
I see there is a Dash-to-Plank extension now ,too.

I decided to reinstall.
Everything is a lot snappier  now. Something must have partially borked the previous install.

I have a suspicion it may have something to do with the Firefox snap not allowing the gnome shell integration extension to function.
This time I immediately uninstalled the snap and replaced it with the package from the repos.
The Firefox snap would not let the browser integration for keepass to function ,either.

---

### Post by Dennis N on 2021-12-10
> I see there is a Dash-to-Plank extension now ,too.
That's interesting. I will have a look at it and see how well it works. 
> I decided to reinstall.
Yes, that's always an option. So, it is not a bug. On 21.10, there are still some visual glitches on the dock like the background not filling in the frame, or an icon's space running over the edge or misaligned. I keep waiting for updates to fix these things, but the extensions are at the mercy of the individual who made them.

---

### Post by Paulgirardin on 2021-12-10
I have an update.

The problem seemed to have been related to having the mounted volumes appear in the dock.
On my original install of 21.10 ,I manually added the following to fstab to mount additional internal drives:
```
# /dev/sdb
UUID=9bca5259-b6b6-47e2-8df2-25ec5bea5696 /mnt/sdb      ext4      defaults        0       0
# /dev/sdc
UUID=02f05beb-2618-412c-9930-e0535185d999 /mnt/sdc        ext4    defaults        0       0
```

I had used this method for every fresh install going back into the depths of time.

This time I just used the Gnome Disks GUI to make the disks mount at startup.

This worked fine but I didn't want these volumes appearing in the dock but I did want USB volume to appear.
So ,in Gnome Disks I removed 'x-gvfs-show' from the mount options for the two volumes.

As soon as I did this, the lag came back.

I added 'x-gvfs-show' back into the mount options and the lag disappeared again.

I can live with the drive icons in the dash.

---

### Post by Dennis N on 2021-12-11
I turned on "Show mounted volumes and devices" in dash to dock to see the behavior. I plugged in a USB and I also have a 2nd internal drive. Only the USB shows on the dock, not the 2nd internal drive,  which seems correct behavior.
```
dmn@Sydney-vm:~$ space
Filesystem     Type  Size  Used Avail Use% Mounted on
/dev/vda1      ext4   28G   21G  5.3G  80% /
/dev/vdb1      ext4   20G  2.5G   17G  14% /mnt/Common-Files
/dev/sda1      ext4   15G  8.9G  4.9G  65% /media/dmn/MyData

```
vdb is 2nd internal drive, sda is external SATA USB.

I notice you are mounting disks formatted ext4 without using partitions. You have done that in the past without any problem? You also don't have file system checking enabled on those drives. The last field of the fstab entry should be 1 or 2, not 0.

---

