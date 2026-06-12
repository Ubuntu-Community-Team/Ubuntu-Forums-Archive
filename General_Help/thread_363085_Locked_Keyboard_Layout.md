---
title: "Locked Keyboard Layout"
date: 2007-02-16
forum: General Help
---

### Post by bennybobw on 2007-02-16
I was running Dapper Drake before and I just did a clean install of Edgy, and added the Spanish keyboard layout.  
The Spanish accent keystrokes in Dapper worked fine, but with my new install of Edgy, they were coming out separate e.g. ´a, ´e, ´i, ¨u
I installed Spanish language support and restarted and that didn't work.

So I followed the directions in [this post ]("http://ubuntuforums.org/showthread.php?t=308854&highlight=spanish+accents")by typing setxkbmap es in a terminal window.

Now my Keyboard Layout Indicator in the Gnome panel is frozen and I can't switch back and forth between keyboard layouts. Furthermore, it says USA when I'm actually using Spanish.

1) Why can't I switch keyboard layouts anymore?
2) Isn't there a better solution?  Why doesn't the Spanish keyboard layout work by default!? I had the same problem in Breezy Badger!

Thanks.
bennybobw

---

### Post by phineaus on 2007-04-22
bennybobw,

I have always had the same problem since I started using UBUNTU (6.10).  I just finished installing feisty, and I was hoping my accent key would finally work...it didnt.  In my case I was starting to think it was an issue with the hardware I had identified...105 key generic international...even though I am using a Toshiba laptop keyboard.  

However, after trying the command line method, it finally works!  Asì!  But, of course, I am having the same problem that you had.  Although I can type setxkbmap us to switch it back to US english...I just cannot use the GNOME keyboard indicator to change it anymore.  What a rare problem!

Anyone have any ideas as to what might be the problem?  We cannot be the only two user to experience this.  

Also, this is probably a little bit picky, but the accent I am getting is backwards from the one that is written in standard spanish....

Peace,
phineaus

ps. I read the man page for setxkbmap, and that gave me no clues as to specifying various keyboard layouts...

---

### Post by phineaus on 2007-04-24
Here are a couple of things I discovered...to at least clear up my own issue regarding this thread.  Gotta love when you end up answering yourself!

1st...if you are only looking to use accents, and dont mind having the rest of the keyboard layout as US english, you can select US English International in the keyboard layouts.  This was the first thing I did.  

2nd...in all the UBUNTU spanish keyboard layout options, including us_intl, the apostrophe key is my accent key, not the [{ key like it is in a similar layout in Windows.  The main reason that I never discovered this was that it was the only key on my keyboard that was not working....I spilled juice in it about 2 months ago.  So, after dismantling the thing and messing with the connector under the key with a screwdriver...I can get the accents I want.  Como así.  

I hope that helps someone else, somewhere else, somewhere down the line.  

phineaus

---

