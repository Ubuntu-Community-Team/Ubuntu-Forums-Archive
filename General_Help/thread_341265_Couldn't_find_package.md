---
title: "Couldn't find package??"
date: 2007-01-18
forum: General Help
---

### Post by icehammer on 2007-01-18
I'm a newbie and have installed ubuntu for the first time..
i wanted to download audio codecs, so i did:
```
sudo apt-get install gstreamer0.10-pitfdll gstreamer0.10-ffmpeg gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse gxine libxine-main1 libxine-extracodecs ogle ogle-gui
```

and i got..
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer0.10-pitfdll
```

This is not only with pitfdll, happening to every package, even if i'm doing it individually..why??
PS: i've checked all options in the synaptic > repositories..

---

### Post by taurus on 2007-01-18
Make sure you have enable both universe & multiverse in synaptic first.  And don't forget to hit the reload button.

---

### Post by mb26 on 2007-02-08
i also have this problem!!
multiverse and universe are checked, and i have reloaded.
also tried using both main server and nearest.

what can i do-- this is v frustrating!

---

### Post by jermor on 2007-02-10
To fix it in Edgy, go to System->Administration->Synaptic Package Manager.  Click on "Settings" and select "Repositories".  Check the box that says "Software restricted by copyright or legal issues".  Then type the command in the terminal again.  It should work this time.  Let me know if you have any problems.

---

### Post by ProfessionalNewbie on 2007-02-11
Hit "reload" dude.

That is, hit "reload" in synaptic package manager.

You could also do the whole thing in the [cli]("http://en.wikipedia.org/wiki/Command_line_interface") & avoid going to the gui by typing in the terminal "sudo apt-get update" & waiting for this to finish then retry your above sudo apt-get install command. 

It worked for moi!

-pn.
"sigh ... after all these years still only a professional newbie at linux"

---

