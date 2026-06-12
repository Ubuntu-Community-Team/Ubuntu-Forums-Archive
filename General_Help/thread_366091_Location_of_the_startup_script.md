---
title: "Location of the startup script"
date: 2007-02-20
forum: General Help
---

### Post by Scotty562 on 2007-02-20
Here is a quick background of what I'm facing. I updated my beryl and now I have a white screen. I searched how to fix the white screen but first I need to delete the startup script that is starting beryl every time I boot my machine. 

The problem is I have no idea where this script is. I would like to manually edit it and take the command that starts beryl out. 

From now on I will manually be starting beryl = /. And I'm still confused why simply updating it broke it to begin with, but that's another issue.

---

### Post by Ryzzen on 2007-02-20
When you get to the login screen, you should see Options in the lower right-hand corner.

I believe you go to Choose Session... and then select GNOME instead of xgl.
Log in, and it should prompt you whether you want to make GNOME your default or not.

Hopefully that will work, and you won't need to edit the startup script.

Also, once you get into Ubuntu, this is the method that worked for me:

> Open synaptic package manager, search for beryl, press ctrl+e and select version 0.1.99.2 you have to do this for beryl, beryl-core, beryl-manager, beryl-plugins, beryl-plugins-data, beryl-settings, beryl-settings-binding, libberyldecoration0 and libberylsettings0

Only change the ones listed. Don't touch any of the ones that say Emerald.

Hope that helps. ^^'

---

### Post by Scotty562 on 2007-02-20
I should have mentioned when I tried logging into a different session I get a gray checkerboard desktop with a black X as a cursor and then it just sits there.

Ok, good news :). I got beryl to crash somehow and it reverted back to metacity . I have it deleted now.

---

### Post by Ryzzen on 2007-02-20
Awesome! I'll have to remember to try crashing things next time I have a problem. ;P

I can't wait for Beryl to release their final, non-buggy version of 0.2.0. *want*

Beryl kind of reminds me of when I got my cell phone...
I didn't need it until I got it, and then I couldn't live without it. @.@

---

### Post by Scotty562 on 2007-02-20
Yeah... exactly... I'm thinking about just upgrading until it eventually gets fixed.

Edit: I ended up reinstalling 1.99.2 (thanks for the tip) I still had the white screen an it drove me nuts for a while but I eventually found a bandaid.


thnogueira said:
"I solved your problem running:

Code:

$ beryl-manager --no-force-window-manager

and then:

Code:

$ beryl-xgl --use-copy"

---

### Post by Scotty562 on 2007-04-19
I updated to feisty and forgot to turn off Beryl now the startup script tries to start it every time the computer boots. I need to find the startup script and remove beryl. Where is this thing?

---

