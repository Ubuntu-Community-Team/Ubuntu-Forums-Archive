---
title: "Extremely lonh boot time"
date: 2007-04-27
forum: General Help
---

### Post by leashy on 2007-04-27
Something just happened and now my Ubuntu is taking probably 6-7 minutes to boot up. After i enter my password, it gives me [this]("http://ubuntuforums.org/g/images/284412/1_Screenshot.png")
 instead of the normal few folders it displays on boot up. It hangs on that screen for about 5 minutes before it will show my panel bars, etc.

The only thing i have done was I installed gDesklets and added it to the startup manager. After i saw that it was taking forever to boot, i uninstalled it. But it is still taking forever.

Anyone have a clue? Im a noob. Whats up all those folder icons on the screen shot above??

---

### Post by binarybird on 2007-04-27
Once the desktop gets loaded do you notice any other issues? Windows not being drawn correctly, color issues? Any display issues? 

Can you post your .xsessions-errors?

open up a console and then enter:

make sure you are in your home folder. It should drop you there by default.

$ **less .xsessions-error**

(make sure to put the period in front of the "x" as this is a hidden file).

Then copy/paste the contents to this thread. Will be happy to take a look :)

---

### Post by leashy on 2007-04-28
I've figured it out. For some reason ubuntu was never really getting shut down completely (I was having to reset it every time because it would hang on shutdown). Now that i've fixed that, i think it unloaded all of the apps that were still in memory. So its booting up perfectly now.

---

