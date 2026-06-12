---
title: "ugly bird follwing me everywhere"
date: 2012-11-27
forum: General Help
---

### Post by sdowney717 on 2012-11-27
It is on every web page I visit. Plastered right in the middle of the page.
It flashes and displays haphazardly
And it is somekind of super imposed add from wingo Turkish airlines.
It first showed up after visiting yahoo finance.

---

### Post by pqwoerituytrueiwoq on 2012-11-27
tracking cookie, pic 5 looks like a artifact from another page (flash issue)
go to this location in firefox (i assume you are using it now)
[chrome://browser/content/preferences/cookies.xul](chrome://browser/content/preferences/cookies.xul)

to stop, use adblock/flashblock/noscript and or this
[[img]http://www.zimagez.com/miniature/screenshot-11272012-080610am.php[/img]](http://www.zimagez.com/zimage/screenshot-11272012-080610am.php)

---

### Post by sdowney717 on 2012-11-27
I did a screen cast showing what it looks like on the screen.
It is tarred up if you want to watch a few seconds.

---

### Post by kokoshmusun on 2012-11-27
:-D  I have no solution.  I do recommend Turkish Airlines, though.

---

### Post by zombifier25 on 2012-11-27
> **sdowney717 said:**
> I did a screen cast showing what it looks like on the screen.
It is tarred up if you want to watch a few seconds.

Just an advice, .tar files don't actually compress data. They only pack folders into a single a file, so that they can be compressed into .gz or bz2.

As your your problem, try installing [Element Hiding Helper for Adblock Plus](https://addons.mozilla.org/en-US/firefox/addon/elemhidehelper/). Then click the Adblock Plus icon, choose "Select Element to Hide", choose that ad and click "Add Element Hiding Rule".

---

### Post by SlugSlug on 2012-11-27
Thats a bit odd! 
Theres no place holders for ads on ubuntu forums is there?!

---

### Post by DukeOfMixture on 2012-11-27
> **SlugSlug said:**
> Thats a bit odd! 
Theres no place holders for ads on ubuntu forums is there?!

I edit my hosts file. What's an "ad"? :lolflag:

---

### Post by Habitual on 2012-11-27
Adblock Plus and NoScript.

Done.

---

### Post by sdowney717 on 2012-11-27
I did the simple idea of turning off 3rd party cookies.
Will see if it comes back.

Will flash go away significantly enough to force internet advertisers to use something else and if so what will it be?

---

### Post by sdowney717 on 2012-11-27
> **SlugSlug said:**
> Thats a bit odd! 
Theres no place holders for ads on ubuntu forums is there?!

So then why does it show up, I tell you this add was very annoying, flashing disappearing and reappearing randomly, always right on top and no way to close it.

---

### Post by vasa1 on 2012-11-27
> **sdowney717 said:**
> So then why does it show up, I tell you this add was very annoying, flashing disappearing and reappearing randomly, always right on top and no way to close it.
Mind specifying which browser you use?

---

### Post by sdowney717 on 2012-11-27
That was on firefox ver 17

---

### Post by vasa1 on 2012-11-27
Okay.
Type about:config in your url bar, hit enter, and then in the search box of the page that opens, paste "click" and hit enter.
You'll get a few results.
Look for "plugins.click_to_play;". If the value is false, set it to true.
Restart Fx. Now no Flash will run without your permission. If you still see the bird it isn't Flash.

---

### Post by vasa1 on 2012-11-27
You can check if it's javascript by opening the Contents tab under Edit, Preferences and disabling javascript.

You can check if it's some extension that you've unwittingly installed by starting Firefox in safe mode (under the Help menu option).

Have you completely cleared your cache?

---

### Post by vasa1 on 2012-11-27
> **sdowney717 said:**
> That was on firefox ver 17
oops! I just looked at that image. Where exactly did you get that version of Firefox from? looks like some weird garbage to me.

---

### Post by vasa1 on 2012-11-27
> **vasa1 said:**
> oops! I just looked at that image. Where exactly did you get that version of Firefox from? looks like some weird garbage to me.
My bad. I should have googled first :( Anyway, for whoever's interested:
> The Funnelcake releases are from Mozilla, they are identical to standard releases in function, but have a couple of preferences changed in order to identify a particular version of Firefox that was downloaded over a short period of time. The idea behind this is to assist in identifying usage data for Firefox anonymously, such as the proportion of those who download Firefox who become long term users.

A Funnelcake version will be made available for download from a particular source for a short period of time. Mozilla will then know the number of downloads for that version. It will next count how many times it has been installed by the number of times the "first run" page is loaded for that Funnelcake version. In a subsequent update, it will count the number of Funnelcake versions are updated. All of this data is anonymous, it does not track which computers are using it, instead it keeps track of the number of downloads & updates there are. 
Source: [Chosen answer]("http://support.mozilla.org/en-US/questions/933472")

And it's been in use quite some years.

---

