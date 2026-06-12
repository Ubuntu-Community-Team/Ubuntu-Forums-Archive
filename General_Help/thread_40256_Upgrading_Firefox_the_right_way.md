---
title: "Upgrading Firefox the right way"
date: 2005-06-08
forum: General Help
---

### Post by duffmckagan on 2005-06-08
I want to upgrade my Firefox from  0.9.3 to 1.0.4.

I have downloaded the file from mozilla.org.

I know how to install it, but doin so, (using sh firefox.sh), it won't be recognised by apt-get and moreover, I won't be able to properly uninstall it.

I would like to know is there any way other than this?

There is a similar thing I found in the [**_Ubuntu Linux Wiki:Upgrading Firefox_**](http://www.ubuntulinux.org/wiki/UpgradingToFirefox10)

---

### Post by dataw0lf on 2005-06-08
Why not just dist-upgrade to Hoary?

---

### Post by duffmckagan on 2005-06-08
Can I further backup this downloaded stuff?
I mean the 202MB that will be downloaded......I have posted on this before, but no-one seemed to have replied.

---

### Post by az on 2005-06-08
[QUOTE=duffmckagan]Can I further backup this downloaded stuff?
I mean the 202MB that will be downloaded......I have posted on this before, but no-one seemed to have replied.[/QUOTE]
I guess your other thread was not clear:

"I am currently on my Warty Desktop.

I know it is a bit outdated for now.
So, i would like to upgrade."

Actually, Warty will be suported for another year and a half so it is stil not that bad...


"Upgrading on my comp, says that it should download 207MB of data.
I have a really slow connection over here. (Max. Download Speed = 11kbps)

Will this upgrade process resume, if in any case, my Connection should break."

Yes.


"Moreover, How do I backup this Upgrade?

You see, I am asking many questions about preserving data, due to slow Internet Connection!"

You can copy everything in /var/cache/apt/archive

It would be better to get a Hoary cd and dist-upgrade from that.  Add the cd to you repository list with synaptic (or commandline: sudo apt-cdrom add)

---

### Post by duffmckagan on 2005-06-08
Thats cool.

Thanks.

---

### Post by duffmckagan on 2005-06-08
But again I come to the same point.

Upgrading to Hoary, I don't have the CD (Can't download due to the slow connection.)

Moreover, I can upgrade, but an upgrade just for the sake of Upgrading the current version of Firefox, doesn't sound good.

Is there any way I could just UPGRADE Firefox?

---

### Post by az on 2005-06-08
You may add Hoary to your sources list and just do 
sudo apt-get update
sudo apt-get install mozilla-firefox.

In that case, you may need to download a lot less than 209 megs, and you should keep both Hoary and Warty entries.  Stay away from non-official repositories, because this will get you into trouble.

That is how people run a mixed woody-Sarge or Sarge-Sid system.

Order a cd and dist-upgrade when you receive it.

---

### Post by duffmckagan on 2005-06-08
Yeah, I have already ordered a CD, but they haven't reached me yet. I have done that in the last month or so. I think that Ubuntu will ship CDs, after the lauch of Breezy now.

Moreover, while upgrading to Hoary, (adding Hoary to the souces list......>I don't know how is that done)......Should I be aware of anything that needs to be done? Any disabling - enabling stuff?

---

