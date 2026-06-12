---
title: "Hardy 8.04 and Compiz on dual screens"
date: 2008-05-22
forum: General Help
---

### Post by aleksab on 2008-05-22
Hey!

I've searched and googled everywhere for some help regarding my issue.

I'm running Hardy 8.04, Nvidia (9800GTX) with two DVI LCD screens.
After some trouble getting the nvidia card to work (had to enabled the NoPowerConnectedCheck), everything was sweet. Compiz worked and it was fine.

However, after enabling dual view on my second lcd screen with Xinerama, I could not get compiz to work. I get the famous "The Composite extension is not available".

However, composition extension is enabled in xorg.conf.

After reading this thread: [http://ubuntuforums.org/showthread.php?t=739127&page=11](http://ubuntuforums.org/showthread.php?t=739127&page=11)

It seems it may be cause by Xinerama? Wondering if anybody have solved this?

---

### Post by rune0077 on 2008-05-22
> **aleksab said:**
> Hey!

I've searched and googled everywhere for some help regarding my issue.

I'm running Hardy 8.04, Nvidia (9800GTX) with two DVI LCD screens.
After some trouble getting the nvidia card to work (had to enabled the NoPowerConnectedCheck), everything was sweet. Compiz worked and it was fine.

However, after enabling dual view on my second lcd screen with Xinerama, I could not get compiz to work. I get the famous "The Composite extension is not available".

However, composition extension is enabled in xorg.conf.

After reading this thread: [http://ubuntuforums.org/showthread.php?t=739127&page=11](http://ubuntuforums.org/showthread.php?t=739127&page=11)

It seems it may be cause by Xinerama? Wondering if anybody have solved this?

You'll have to use TwinView instead. Compiz and Xinerama does not seem to work together.It's an issue with the nvidia-drivers, and nvidia should be hard at work getting it fixed (though they have been so for quite a while without any results). Until that's done, use TwinView (or don't use Compiz).

---

