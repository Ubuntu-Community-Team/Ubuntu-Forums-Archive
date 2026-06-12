---
title: "Terminal not starting after profile change"
date: 2008-07-03
forum: General Help
---

### Post by stereo_steve on 2008-07-03
Hey guys,

I was messing around with terminal and saw that there was a field to put in your own script on program start up. 

I typed *echo "hello World"* and saved it. I just wanted to test if it would print that on the screen the next time I started it. 

Unfortunately it will not longer start. I had a look in my .profile and bash.rc and neither contain the text I put in. Can someone tell where its stored and I will remove the text?

Thanks

Steve

---

### Post by gator64 on 2008-07-03
So now you can't open the terminal at all ?  To make this happen, had you checked "Run a custom command instead of my shell" in your terminal profile ?

The profile information is stored here:

~/.gconf/apps/gnome-terminal/profiles

---

### Post by gator64 on 2008-07-03
And to edit this file you can use
gconf-editor

Once you're in there, navigate to apps/gnome-terminal/profiles/Default

---

### Post by stereo_steve on 2008-07-05
Thanks,

I deleted the gnome-terminal folder and reinstalled gnome-terminal. Everythiing is good again!

---

