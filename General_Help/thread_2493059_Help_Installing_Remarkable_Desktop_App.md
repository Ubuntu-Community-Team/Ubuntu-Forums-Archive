---
title: "Help Installing Remarkable Desktop App"
date: 2023-12-01
forum: General Help
---

### Post by blahboybaz on 2023-12-01
I recently bought a remarkable 2 tablet and wanted to install their desktop app but I'm not sure what the best solution is for doing that. There is a snap available; but, as of this writing, was last updated almost a year ago. If I use that I'm concerned whether I'll get all the most up to date features. If I install from the remarkable web site (their official source) I have to run it in wine; which, for me, is a big fat nope! And even running it in wine may be deprecated and not work at all anymore. I don't like the options I'm seeing so far. Is there a better option than the ones I've mentioned so far? If the snap does give me all the latest greatest functionality then I would definitely go for that but I don't know how to tell if that's the case or not. Does anyone have experience with this and could offer some guidance?

Snap (is up to date with latest features?):
[https://snapcraft.io/remarkable-desktop](https://snapcraft.io/remarkable-desktop)

Remarkable Wiki (speaks of running in wine):
[https://web.archive.org/web/20230604031356/https://remarkablewiki.com/tips/client](https://web.archive.org/web/20230604031356/https://remarkablewiki.com/tips/client)

Remarkable Help Page (may not be available for linux now):
[https://support.remarkable.com/s/article/Desktop-app](https://support.remarkable.com/s/article/Desktop-app)

[B][I]Running Ubuntu 22.04.3 on an HP Envy laptop

[/I][/B]

---

### Post by Br11 on 2023-12-11
did you manage?

---

### Post by blahboybaz on 2023-12-21
> **Br11 said:**
> did you manage?

Not yet

afaict there is not solution so I've resorted to shaming the folks at reMarkable for excluding us..

 :popcorn: anyone?

---

### Post by Holger_Gehrke on 2023-12-22
The snap is just a really big bash script named "sommelier" packaged as a snap that can download the Windows version and configure wine (installed as a snap, of course) to install and run that.

Running Windows software with wine can often work quite well, especially if the developers of the software intended the program to be run this way.

Holger

---

### Post by blahboybaz on 2023-12-27
> **Holger_Gehrke said:**
> The snap is just a really big bash script named "sommelier" packaged as a snap that can download the Windows version and configure wine (installed as a snap, of course) to install and run that.

Running Windows software with wine can often work quite well, especially if the developers of the software intended the program to be run this way.

Holger

I see! Well, personally, I have a very strong aversion to using wine. Maybe its because of my experience with it back in the day when it was fairly new and very VERY glitchy - idk. Maybe I'm a fool but I think it would take some kind of act of God or something to get me to change my mind. I do sincerely appreciate finding this out tho.

---------------------------------------------------------------------------------------------------- Update ----------------------------------------------------------------------------------------------------

Fwiw I did end up trying [the snap]("https://snapcraft.io/install/remarkable-desktop/ubuntu"). The snap installed; then, when I launched remarkable-desktop wine said it was installing the .exe but was taking forever so I went back to a project I'm working on and about 45 min passed before I though about it again. When I went back there was still the progress window with wine installing the .exe (still). It looked like nothing had changed. So I closed the window and removed remarkable-desktop. It's a real shame. Remarkable is built on open source even with an embedded linux distro as the foundation of it all and they can't make a linux port of their desktop app available. They force you to pay for features and then cut out a whole segment of users. Even if you do pay - if you are a linux user - you still won't have the privilege of some of the most useful features.

---

