---
title: "Unity Greeter Wallpaper - reset to default?"
date: 2014-09-10
forum: General Help
---

### Post by mykrob on 2014-09-10
Running Ubuntu 14.04 on a Toshiba laptop, a Satellite E45-B4200 to be exact.

If I set the wallpaper to a picture that I downloaded, it looks fine on the desktop, however, the Unity Greeter wallpaper seems to go back to the default ugly purple wallpaper. If I choose one if the wallpapers that comes with Ubuntu, the greeter changes to match. 

What's the magic trick to make this behavior follow custom wallpaper?

---

### Post by Frogs Hair on 2014-09-10
The greeter should display the selection for the desktop background and splash screen will remain purple. Have a look at the following post. [http://askubuntu.com/questions/455849/unity-greeter-does-not-display-custom-wallpaper](http://askubuntu.com/questions/455849/unity-greeter-does-not-display-custom-wallpaper)

---

### Post by mykrob on 2014-09-12
Yup, that's the way it *should* work, but it isn't. If I select a custom wallpaper from my Pictures folder, it works fine for the desktop but not for the login/greeter screen. The boot splash does as it should. 

I know it's not a big deal, it just use to work right, then for no reason, seems to have stopped, and the greeter reverts to the ugly default background if I choose a custom wallpaper.

---

### Post by mcduck on 2014-09-12
Make sure that both the wallpaper image itself, and your Pictures folder (plus any subfloder where the wallpaper might be) all have read permissions for "others". The folders might also need execute permission.

Without the read permission the login screen won't be able to access the image and will use the default one instead.

I'd also assume having encrypted hhome dirctory would also stop the login screen from accessing the image, at least I can't see how it could possibly access it in that situation :D

---

