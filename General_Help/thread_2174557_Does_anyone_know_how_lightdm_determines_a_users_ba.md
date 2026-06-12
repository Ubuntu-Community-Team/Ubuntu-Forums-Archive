---
title: "Does anyone know how lightdm determines a users background has changed?"
date: 2013-09-15
forum: General Help
---

### Post by CaptainMark on 2013-09-15
When using Unity on Ubuntu and you change your background then the login background changes to match for your user (I'm sure most of you know that), my question is:
How does lightdm detect the user has changed his/her background?

The reason I'm asking, if that helps clear up what I'm actually asking, is: I use the Cinnamon desktop environment and it DOES NOT update the user background on lightdm so whatever happens in Unity and Gnome-Shell and XFCE when you change your wallpaper that allows lightdm to display the same wallpaper is NOT happening in Cinnamon and I want to report it as a bug against Cinnamon, it should be compatible with such a popular display manager as lightdm.
 
I've been hunting through gconf and dconf settings thinking it might be a setting in there that should be updated whenever the wallpaper changes but I cant find the answer.

Also just to clarify I'm not looking for a temporary workaround like logging into Unity and changing the wallpaper there, I know I could do that but I'm aiming to fix this at the source without having to depend on installing any more packages than necessary that way it can be fixed on all systems regardless of which distro is being used and what other DE's are installed.

Thanks for any help
Regards 
Mark

---

### Post by steeldriver on 2013-09-15
It's controlled via the unity-greeter draw-user-backgrounds key I think - but the one belonging to user lightdm, not the user whose background it is displaying

```
com.canonical.unity-greeter draw-user-backgrounds true
```

If you want to play with it and see, you can do something like

```
sudo su -s /bin/sh lightdm -c "gsettings get com.canonical.unity-greeter draw-user-backgrounds"
```

to view the current value, and

```
sudo su -s /bin/sh lightdm -c "dbus-launch --exit-with-session gsettings set com.canonical.unity-greeter draw-user-backgrounds true"
```

I don't know what greeter is used for cinnamon - gtk-greeter? - or whether there is an equivalent parameter

---

### Post by CaptainMark on 2013-09-15
No this isn't what I mean, this only tells Lightdm to look (or not look) for a users background, it's already set to true but my aim is to find out why in Cinnamon it does not work yet it does with Unity,Gnome-shell-Xfce,Kde etc etc. I'm trying to identify what setting it is that all these other DE's change but Cinnamon does not.

So to clarify my question: 
Scenario 1: I log into Xfce and change my wallpaper, when I log out lightdm has updated my wallpaper to match
Scenario 2: I log into Cinnamon and change my wallpaper, when I log out lightdm has NOT updated my wallpaper to match and will still remain the same as before

What is happening behind the scenes that makes scenario 1 & 2 different, Xfce is doing something that Cinnamon is NOT doing to update the wallpaper in lightdm. Something that lightdm is watching for and monitoring, I aim to find out what that 'something' is

---

### Post by vasa1 on 2013-09-15
Is it possible that Mint does things slightly differently?

---

### Post by CaptainMark on 2013-09-15
> **vasa1 said:**
> Is it possible that Mint does things slightly differently?
My question does not regard Mint,

EDIT: Okay to some extent that is false, but to clarify I am not using Mint, I am using Cinnamon on Ubuntu, the people I intend to take this issue to are the Mint developers but I'm querying the workings of Lightdm, once I've found out how Lightdm behaves I will take my issue to the Cinnamon Devs.
I don't feel this belongs on the Mint forums though, and I hope this post doesn't get dismissed as off topic, I often find on here as soon as a package that is not strictly in the Ubuntu standard install gets mentioned people get told to go seek help elsewhere even if the question does concern Ubuntu and its default packages, forgive my bluntness but I see this happen a lot here.

I also have an issue report open on Github against Cinnamon [here]("https://github.com/linuxmint/Cinnamon/issues/2379") but would like help detailing it more to increase the likelihood of having it fixed

---

### Post by mc4man on 2013-09-15
Well obviously you need to use the unity greeter.
Then it would depend on what version is being used.

Prior to 13.04 the info was handled by gnome-settings-daemon's background plugin.
Starting in 13.04 that plugin was made inactive which initially caused the greeter's use of a custom background to fail. 
The fix there was to use nautilus > accountservices to provide the info to unity-greeter

Basic info concerning the above switch can be found in these reports
[https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619](https://bugs.launchpad.net/ubuntu/+source/ubuntu-settings/+bug/1122619)
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1128492](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/1128492)

---

### Post by CaptainMark on 2013-09-15
Thank you mc4man this is what I was looking for and now works as expected. Ill take this and see what I can do with it

---

