---
title: "guification help"
date: 2007-03-12
forum: General Help
---

### Post by fleshberkowski on 2007-03-12
i just switched to ubuntu from a mac and while i've figured out how to customize some of the things to my liking, there's one thing that i can't figure out. in gaim, i wanted to set a feature similar to growl in osx, or even how aim and gtalk on xp have floating notification windows that pop up and fade away with the content of the im in them. i've managed to configure guification to tell me when people are signing on or messaging me, but not the actual content of the ims. instead i get "chris has messaged you". which isn't very helpful.  is there anyway to display this? i figured in guification plugins i'd need to check off "im message" but that didn't do it. any info would be greatly appreciated. 

also, is this something that maybe kubuntu and kde would handle better? i've been thinking about installing it but wanted to get a better grasp of ubuntu and gnome before i got even more confused.

---

### Post by bollix47 on 2007-03-12
I used the information on [_this page_]("http://repository.debuntu.org/") to install Gaim 2.0.0 Beta 6 which has the message in the pop-ups.

---

### Post by fleshberkowski on 2007-03-12
ok, i tried info on the page you gave me, and i got this error: W: GPG error: [http://repository.debuntu.org](http://repository.debuntu.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 0E466170BCF1FC29

so i went into synaptic and added multiverse to my repositories and upgraded gaim. now, in gaim my guifications were disabled and it says: 

Error: You are using gtk-gaim, but this plugin requires gtk. Check the plugin website for an update.

has anyone had this problem before? what else can i do?

---

### Post by bollix47 on 2007-03-12
Did you install gaim-libnotify?

Also, it tells you how to add the appropriate key on the same page mentioned above.

---

### Post by fleshberkowski on 2007-03-12
libnotify worked like a charm.  for some reason, i could've sworn i already installed it. regardless it worked and i'm happy. thanks so much

---

### Post by bollix47 on 2007-03-12
You're welcome.  Glad you got it working the way you wanted it.

Adding that key will stop those warning messages when you reload in synaptic or do an apt-get update.

---

