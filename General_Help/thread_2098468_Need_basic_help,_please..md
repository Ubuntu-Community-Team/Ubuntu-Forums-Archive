---
title: "Need basic help, please."
date: 2012-12-26
forum: General Help
---

### Post by noelllll on 2012-12-26
Hey okay so I'm really new to this whole Ubuntu thing.
Uninstalled Windows about a week ago and have been playing with this ever since.
Just got Gnome3x? I think? And the toolbar on the left side is not there anymore.
Also, there is no time or volume or network or anything at the top bar anymore.
Need some basic tips to customize things on here. Or should I just go back to the original desktop that came with it?
Using 12.10 by the way.
I have attached a screen shot with just the background for now, will post anything else you may need to help.
Please and thank you.

---

### Post by noelllll on 2012-12-26
bumping for anything
anything at all..

---

### Post by fdrake on 2012-12-26
let's see if an update fixes it:
```


sudo apt-get update
```

if you cannot breng the terminal go into console mode:
how to enter console : ctl +Alt+f1 (or f2,f3,..)
hot to exit:   ctrol+alt+f7
restart

------------------------
edit your are currenlty using gnome 2 not 3:
logout and slect at the login screen gnome unity  [http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop)
look at screen shoots. in section 8/9

---

### Post by oldos2er on 2012-12-26
> **noelllll said:**
> bumping for anything
anything at all..

Please give people time to respond, and don't bump your post more than once every 24 hours. Thanks.

---

### Post by noelllll on 2012-12-26
> **fdrake said:**
> let's see if an update fixes it:
```


sudo apt-get update
```

if you cannot breng the terminal go into console mode:
how to enter console : ctl +Alt+f1 (or f2,f3,..)
hot to exit:   ctrol+alt+f7
restart

------------------------
edit your are currenlty using gnome 2 not 3:
logout and slect at the login screen gnome unity  [http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop](http://complete-concrete-concise.com/ubuntu-2/ubuntu-12-04/ubuntu-12-04-how-to-install-the-gnome-desktop)
look at screen shoots. in section 8/9

okay well that worked I think?
Looks awesome now.
Thank you very much kind sir.

Also @oldos2er, sorry, first time posting. I'll be sure to keep that in mind next time.

I attached a screenshot of what it looks like now. Is that all?
Now I could go around looking for themes and trying to figure out how to apply them?

---

### Post by kaldor on 2012-12-26
> **noelllll said:**
> okay well that worked I think?
Looks awesome now.
Thank you very much kind sir.

Also @oldos2er, sorry, first time posting. I'll be sure to keep that in mind next time.

I attached a screenshot of what it looks like now. Is that all?
Now I could go around looking for themes and trying to figure out how to apply them?

Looks good to me :)

What you're looking for right now is GNOME *Shell* themes. Themes for older versions of GNOME aren't going to work.

I recommend searching Deviantart. There are lots of beautiful Shell themes there. Also, GNOME Shell uses CSS. This makes it very easy to make your own custom themes.

---

### Post by fdrake on 2012-12-26
yep. that's how it supposed to look like!

---

### Post by noelllll on 2012-12-26
> **kaldor said:**
> Looks good to me :)

What you're looking for right now is GNOME *Shell* themes. Themes for older versions of GNOME aren't going to work.

I recommend searching Deviantart. There are lots of beautiful Shell themes there. Also, GNOME Shell uses CSS. This makes it very easy to make your own custom themes.

Hm, alright cool sounds good.
I know pretty much all about CSS so this could be fun.
Where would I look to play around with that?
Or should I just find some themes first to kinda understand how everything works?

---

### Post by kaldor on 2012-12-26
> **noelllll said:**
> Hm, alright cool sounds good.
I know pretty much all about CSS so this could be fun.
Where would I look to play around with that?
Or should I just find some themes first to kinda understand how everything works?

On Linux, themes are stored in a hidden folder in your Home directory called *.themes. *Inside that you can place extra themes. For this reason, I recommend you copy the default GNOME Shell theme into that and tweak it there.

Inside your Home folder, press Ctrl H to show hidden files. Go to *.themes*

Then, create a folder inside there with the name of your new theme. Call it "MyTheme" or similar. 

Go to /usr/share/gnome-shell. You will see a directory called "theme". Copy this folder into your "MyTheme" folder. Rename "theme" to "gnome-shell".

Then, you can get started on making your own theme. Install gnome-tweak-tool to switch themes easily :

```
sudo apt-get install gnome-tweak-tool
```

Have fun :P

---

