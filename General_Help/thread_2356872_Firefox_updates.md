---
title: "Firefox updates"
date: 2017-03-27
forum: General Help
---

### Post by no2498 on 2017-03-27
man ive been out of the loop way to long. this is what's wrong with this computer
can we take fire fox out /off the list in the source list to stop updates 
i do not use fire fox or chrome any ways
ill be back in a few days to fix my computer
ill need to set the color in my terminal to like black so i can see what is typed
as of now it is clear 

john

---

### Post by oldos2er on 2017-03-27
Post moved to its own thread. 

Please create a new thread rather than "hijacking" someone else's;  it will have greater visibility.

---

### Post by Impavidus on 2017-03-28
You can uninstall firefox, if you wish. Just use the package manager, then autoremove its dependencies.

---

### Post by &amp;KyT$0P# on 2017-03-28
I'm not quite sure what you're trying to do.  If you want to "lock" the Firefox version to what you have now, you can use [FONT=Courier New]apt-mark[/FONT] to put the Firefox package(s) on hold.  Refer to [FONT=Courier New]man apt-mark[/FONT] for more info.

---

### Post by no2498 on 2017-03-30
no i got the update that fire fox did away with with support for 32 bit flash player

now i just need to come back and ask how to fix it. so i can git in to some flash sites i go to

john

---

### Post by &amp;KyT$0P# on 2017-03-30
> **no2498 said:**
> no i got the update that fire fox did away with with support for 32 bit flash player

now i just need to come back and ask how to fix it. so i can git in to some flash sites i go to

john

Does [this]("https://ubuntuforums.org/showthread.php?t=2355983") help you?

---

### Post by no2498 on 2017-04-01
yes thats the post they moved my post from lol

ok how do i get this done
i need the codes and things to put in the terminal

Yes, the Firefox update is the source of the problem. There are a few possibilities -

 1) Downgrade Firefox to version 51 or the latest 45 ESR

 2) Switch over to Firefox 52 ESR and enable loading plugins other than Flash -
 about:config > set plugin.load_flash_only to false

the one that works the best
john

---

### Post by &amp;KyT$0P# on 2017-04-01
Please use quote tags when quoting stuff I wrote, thanks.  (add [noparse]"> " at the beginning and ""[/noparse] at the end)

> **no2498 said:**
> the one that works the best
I would think switching to Firefox 52 ESR would be the safest option.

Terminal commands are not required.  You just download Firefox 52 ESR from the link I provided, and then extract it somewhere.  I usually extract it in my home folder, such that I run Firefox with [FONT=Courier New]~/firefox/firefox[/FONT] .

Once Firefox 52 ESR is installed, type [FONT=Courier New]about:config[/FONT] in Firefox's location bar and hit Enter.  If you get a warning about voiding your warranty, just click the button to dismiss it.  Then find the [FONT=Courier New]plugin.load_flash_only[/FONT] entry, and double-click it to set it to [FONT=Courier New]false[/FONT].

You might need to restart Firefox for the change to take effect.

---

