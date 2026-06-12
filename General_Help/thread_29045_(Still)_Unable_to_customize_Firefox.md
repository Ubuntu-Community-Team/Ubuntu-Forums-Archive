---
title: "(Still) Unable to customize Firefox"
date: 2005-04-22
forum: General Help
---

### Post by Annie Versary on 2005-04-22
Hi there,

as already described [here](http://ubuntuforums.org/showthread.php?t=27741) I still can't install extensions and/or themes to the firefox I've installed via apt-get. Some online resources keep telling that the F minds if it's installed to an inappropriate directory and in the meantime there are some reviews that refer to it as an [unique (K)Ubuntu issue](http://os.newsforge.com/os/05/04/19/200205.shtml?tid=152&tid=2) (the "Bugs and Missing Features" paragraph).

Though I'm quite sure that those problems do exist under other distros either: does anybody know if there is a solution yet?

Thanks in advance...

Annie

---

### Post by shakin on 2005-04-22
Try this:

1. Remove firefox and related packages using Synaptic.

2. Backup your bookmarks then delete your firefox home directory (~/.mozilla/firefox/)

3. Re-install 1.0.2 from the repository.

4. Run as root the first time (sudo firefox). Install an extension and see if that works. Hopefully it does, then continue onto the next step.

5. Now run as your user and try to install an extension.

If that doesn't solve your problem, try chmodding the firefox install directory to give your user read/write priviledges.

Your last scenario is to remove firefox again using synaptic and install 1.0.3 from mozilla.org. There are instructions in the how-to forum if you need them.

---

### Post by wolfja on 2005-04-22
this is how i upgraded to firefox 1.0.3 in ubuntu 5.04

first i uninstalled the version that came with ubuntu by typing
     "sudo gnome-app-install" in Terminal then entering my password this brings up your application installer click on "internet" and you will see mozilla firefox checked. you want to uncheck this. then click "apply" this will uninstall firefox. then i downloaded firefox 1.0.3 off the web. and untarred it  into the /usr/lib/ directory then on the menu bar at the top in gnome 2.10 i right clicked the icon next to "system", this is where firefox used to be at then i clicked on properties and in the command box i clicked the browse button and pointed the directory to /usr/lib/firefox-installer/firefox then i set the icon to the firefox one and wholla!!! im now using 1.0.3 without a hitch i can update my themes etc. etc.

---

### Post by martigan on 2005-07-13
Hi

I had to type in firefox about:config then chang the general.useragent.vendorSub value to 1.0.4. After that I was able to download skins and extensions within Firefox.

Somehow this field is updated in the ubuntu distrobution?

Hope it helps someone

Kind regards

Martigan

*edit* Oh I noticed this is an old trhead, still hopes it helps some people ;)

---

