---
title: "How to remove unity sidebar icons?"
date: 2016-09-16
forum: General Help
---

### Post by hal9k-r on 2016-09-16
I did install cairo-dock and want to get rid of the launcher icons bouncy effect at unity launcher.
Here is a video showing the problem: [https://vid.me/dsln](https://vid.me/dsln)

Edit: Im at ubuntu 16.04, cairo-dock working with opengl and unity.

---

### Post by RobGoss on 2016-09-17
Hello and welcome. I was able to find this thread how to[ disable all unity animations]("http://askubuntu.com/questions/138622/how-to-disable-all-unity-animations") this may help you with your question, about half way down the page there's a post advising to use **compiz-settings manager **to alter the animations for the launcher 

best of luck

---

### Post by howefield on 2016-09-17
Are you talking about the Unity launcher on the left side of the screen ? (and not cairo-dock)

System Settings > Appearance > Behaviour > Autohide and set Reveal sensitivity as low as it will go.

Not sure if that will be enough for you.

---

### Post by deadflowr on 2016-09-17
Somewhere on these forums, a user posted an interesting thread with a convoluted method of removing the launcher from unity.
It involved downloading the source code for unity and doing some basic editing of a few files, then recompiling the source and installing it.
(But that was probably well over a year ago, and I forget what the thread was called, and it's unclear whether or not it would even work on 16.04)

((Not that that is helpful in any way shape or form, just putting it out there that someone did find a rather messy way of removing the launcher, if you really want to go down that rabbit hole, you can at least know that a method did at some time exist to do that, though it does come off as a " I know a guy who knows someone who went to school with a girl whose uncle was the roommate of the brother of blah blah", so sorry about that))


That said, cairo-dock should have installed a stand-alone user session that you can choose to run from the login screen.
At least it has always done so for me.
In which case you can login to that session and run cairo dock without any unity cruft.

But that's my 2 cents, perhaps you have reason to run it within unity...

---

### Post by hal9k-r on 2016-09-18
Thank you very much for you suggestions.
By ccsm I made animation disappear, which help me a little, but i still got the animation in the launcher. Now you can see it in this new video: [https://vid.me/TgcD](https://vid.me/TgcD)
right besides my "back" icon in chromium.

---

### Post by hal9k-r on 2016-09-20
Don't know if this is okay, but I still got the problem and would like to 'bump' the thread.

---

