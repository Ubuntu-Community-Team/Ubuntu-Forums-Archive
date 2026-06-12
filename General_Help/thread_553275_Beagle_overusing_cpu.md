---
title: "Beagle overusing cpu"
date: 2007-09-17
forum: General Help
---

### Post by intense.ego on 2007-09-17
Recently, the process beagled-helper has been eating around 70% of my cpu causing my computer to go very slowly. I read that it could be slow when indexing word files and pdf (which i have). I tried to follow the instruction on the bottom of this page ([http://beagle-project.org/Troubleshooting_CPU](http://beagle-project.org/Troubleshooting_CPU)) but it didn't work. Is there an alternative, and preferable simple, way to do this? Are there any other solutions?

---

### Post by thelocust on 2007-09-17
Google released a Linux version of it's desktop search. I never had much luck with beagle.

---

### Post by intense.ego on 2007-09-17
So, how do I uninstall beagle and install google desktop?

---

### Post by jviscosi on 2007-09-17
I've had this problem with beagle too.  It used to happen when it was indexing Thunderbird e-mails, but lately wmtop has been showing pdftotext as the culprit, as you suggest.  I changed my system to only run the beagled daemon when I have a search window open, which means I sometimes have to let it sit a while before it will find newer documents/e-mails, but usually I'm looking for older ones.

You can uninstall beagle by opening synaptic, searching for beagle, and unchecking it.  You can also do **sudo apt-get remove beagle** from a terminal.  I don't know what, if any, other packages depend on it.  I doubt there are any.

I haven't installed Google desktop but [here's a how-to]("http://www.simplehelp.net/2007/06/28/how-to-install-setup-and-use-google-desktop-search-in-ubuntu/") that looks pretty straightforward.   (It appears to assume that you're using Gnome.)  I wouldn't be surprised if there's an official Ubuntu tutorial floating around somewhere, but a cursory search didn't turn one up.

---

### Post by intense.ego on 2007-09-17
Thank you both very much. I'm going to uninstall beagle and install google desktope right now.

---

### Post by fragos on 2007-09-18
Google Desktop is amazing.  It does a better job of running in the background without grabbing the entire machine like Beagal and others of it's kind do.  Took a few hours to index my system the first time but that didn't impact the performance of my box while doing other things.  It works nicely with browser initiated Google searches as well.  Sweet!!!

---

