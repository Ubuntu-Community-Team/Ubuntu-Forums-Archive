---
title: "Deskbar"
date: 2007-10-20
forum: General Help
---

### Post by Virgofenix on 2007-10-20
Is there a way to restore the old deskbar applet layouts? I was comfortable with it being an embedded line in a panel. The new pop-up window method is a monumental regression in usability.

---

### Post by posterboy on 2007-10-21
Yes, that's been an option since it was included. Right click on the tiny icon, go to preferences, and set it up either way you like.

---

### Post by chrisccoulson on 2007-10-21
The old layout is no longer an option with the new Deskbar in Gutsy. According to the Deskbar roadmap, this feature is going to be re-included again for 2.22 [http://live.gnome.org/DeskbarApplet/RoadMap222]("http://live.gnome.org/DeskbarApplet/RoadMap222")

---

### Post by posterboy on 2007-10-21
Oh, my! I use this daily in my work, I hope surely this will happen, I plan to wait a few weeks on the upgrade, maybe by then, it will be back.

---

### Post by Virgofenix on 2007-10-21
Is it going to be part of a new Gutsy install?

---

### Post by posterboy on 2007-10-21
I would hope that an apt-get upgrade would do it, even though it wouldn't be on the install disk.

---

### Post by chrisccoulson on 2007-10-21
Your only hope of the new Deskbar being in Gutsy would be for it to be backported. The interface changes are targeted for GNOME 2.22 AFAIK, so will be in Hardy.

---

### Post by posterboy on 2007-10-21
Well, shucks, maybe I can get used to it. I certainly can't do without it! Deskbar and beagle are in use here maybe 80-100 times a DAY!

---

### Post by Virgofenix on 2007-10-21
Will probably skip Gutsy then.

I'm wondering, can I fix this myself? I don't know how, but I'm learning some computer languages atm, and this wouldn't be a bad first project for Linux. Anybody care to give tips, leads, or suggestions?

Thanks.

---

### Post by Virgofenix on 2007-10-28
The .deb link in this post is supposedly an older version of deskbar.

[http://ubuntuforums.org/showpost.php?p=3181461&postcount=17](http://ubuntuforums.org/showpost.php?p=3181461&postcount=17)

---

### Post by shaunbarlow on 2007-10-31
Hi all,
I too am one of the millions scouring the globe with high hopes that deskbar as a panel entry field may not be lost forever...
AND I just got it back!
Here's how...

open synaptic, search for deskbar, on the deskbar-applet package click completely remove.
Click apply, wait for it to do it's thing.
Close synaptic.

In terminal type
sudo gedit /etc/apt/sources.list

copy and paste the first few repositories to the end of the file and then substitute the word gutsy for feisty.

Save and close then open up synaptic. go to settings > repositories.
Untick all of the repos in the ubuntu software tab.
Close and reload.
Search for deskbar, u should find deskbar-applet version 2.18.1-0ubuntu2. Install it!
Then to make sure it doesn't disappear on you, search for deskbar again and click on deskbar-applet (just to highlight it) then click Package > Lock Version.

All that's left is to remove then add deskbar back to the panel.
Et voila!

This is a little vague, as I just started fiddling and eventually got things going. So if someone else can be a little more specific as to which repositories need to be added and unticked that would be helpful to many others I'm sure.

Long live the panel entry deskbar!!
Cheers all.
Shaun

---

### Post by Virgofenix on 2007-11-12
[QUOTE=shaunbarlow;3680565

In terminal type
sudo gedit /etc/apt/sources.list

copy and paste the first few repositories to the end of the file and then substitute the word gutsy for feisty.[/QUOTE]

Can we get your entry with "feisty"?

---

### Post by Virgofenix on 2007-11-12
> **Virgofenix said:**
> The .deb link in this post is supposedly an older version of deskbar.

[http://ubuntuforums.org/showpost.php?p=3181461&postcount=17](http://ubuntuforums.org/showpost.php?p=3181461&postcount=17)

I confirm that the .deb in this link works. I now have the old deskbar back. However, just like how the old deskbar doesn't work in entry mode with Beryl, same goes for Compiz Fusion. You'll be forced to use "button in panel" mode but at least that's better than the current one.

---

### Post by GeneW on 2007-11-20
> **Virgofenix said:**
> The .deb link in this post is supposedly an older version of deskbar.

[http://ubuntuforums.org/showpost.php?p=3181461&postcount=17](http://ubuntuforums.org/showpost.php?p=3181461&postcount=17)

That package works perfectly.  Awesome.  I can't imagine what the people who decide on the packages for a release were thinking when they included the new version of the deskbar.  It's a massive regression in utility and is almost too slow to use besides.  I'm very happy to have my old deskbar back.

---

### Post by Virgofenix on 2007-11-21
I've been using it a while. I have run into some trouble regarding compatibility with some updated features (like Tracker). Refer :[http://ubuntuforums.org/showthread.php?t=614245](http://ubuntuforums.org/showthread.php?t=614245)

---

