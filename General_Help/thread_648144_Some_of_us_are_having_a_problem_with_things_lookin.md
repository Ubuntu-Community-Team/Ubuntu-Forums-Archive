---
title: "Some of us are having a problem with things looking washed out."
date: 2007-12-23
forum: General Help
---

### Post by Sabar on 2007-12-23
When I searched for this problem I found a few people who seemed to be having the same difficulties. Figured I would add there posts to this also, so maybe something one of us says sparks something.

When I look at my firefox it Looks ( for lack of a better term ) washed out. there are no brite colors eerything just seems to be mostly white. Like when I am reading posts the lines betweens posts are barely there and the tan part where the posts are sticky is very very light. like to the point yoiu have to look to notice it is tan.

Anybody have any idea what this could be?

Here are the other two posts that are similar to mine.

> [http://ubuntuforums.org/showthread.php?t=647551](http://ubuntuforums.org/showthread.php?t=647551)

[http://ubuntuforums.org/showthread.php?t=580121](http://ubuntuforums.org/showthread.php?t=580121)

Thank you for any help we can receive 
Sabar

---

### Post by adam.tropics on 2007-12-23
Screenshot might demonstrate your problem better.

---

### Post by oscarsfriend on 2007-12-23
Is this just the text, or are images the same too?  If it is just the text try changing the default fonts from within firefox.  Also, if you have a nvidia graphics card you could try using the nvidia settings tool to try adjusting the colour vibrancy.

---

### Post by Sabar on 2007-12-23
I have an ATI Radeon X550 256mb PCIE Graphics Processor

unfortinatly not sure how to get a screen shot on here. what firefox setting would I adjust?

Thanks for the posts
Sabar

---

### Post by adam.tropics on 2007-12-23
Screenshot is in the accessories menu, or just hit <print> on your keyboard I believe.

edit: or do you mean unsure how to post it?

---

### Post by Sabar on 2007-12-23
not sure how to post it
but I will be giving it a try

---

### Post by Sabar on 2007-12-23
not sure how to post it
but I will be giving it a try

OK I think I have it posted please let me know what it looks like to you guys

---

### Post by oscarsfriend on 2007-12-23
> **Sabar said:**
> unfortinatly not sure how to get a screen shot on here. what firefox setting would I adjust?

From fireforx: edit->preferences->content, then set default font, and click advanced (in same section) and set each font here also.

EDIT: but seeing your screenshot, I don't think that is going to help because it looks perfect to me!  Maybe you need to adjust the settings on your monitor?  Or maybe check the cables?  Does it do this with all programs?

---

### Post by p_quarles on 2007-12-23
> **Sabar said:**
> not sure how to post it
but I will be giving it a try

OK I think I have it posted please let me know what it looks like to you guys
To me, that screenshot looks perfectly normal. Are you sure that your monitor isn't the culprit here?

---

### Post by Sabar on 2007-12-23
Well I tried to adjust the monotor but to be honest it looks like it is affecte the ubuntu pages the most possable becouse of the light colors??

I have no clue what is going on.

---

### Post by Cubby on 2008-02-19
Hi,

I know this thread is a bit dated, but I just discovered that I can have clear fonts in Ubuntu Feisty Fawn, 

The black fonts looked a bit faded, kinda like black ink bleeding onto paper, and especially noticeable while using Firefox browser as well as terminal output.  

First thing I did was change the gamma because I noticed the contrast was too high, making the desktop look a bit washed out.

To change it temporarily, use xgamma:

$ xgamma -gamma 0.8

For my screen, I prefer 0.8 and so I made this a permanent setting by the following command and editing the xorg.conf file:

```
sudo gedit /etc/X11/xorg.conf
```

add a line in xorg.conf, in the monitor section:

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Gamma           0.8 0.8 0.8
EndSection

click "save" and close the file.  When you reboot, you'll notice the contrast is what you changed it to.

But, still fonts in Firefox looked blotchy.  For some reason, Konqueror fonts looked crisper, so I ended up using that browser and removing Firefox.  Then I decided to give Swiftweasel browser a try, and though the fonts were still washed out looking, I decided to keep this browser along with Konqueror, as I use both for different reasons.  

Finally I found what made the difference for my LCD monitor.  

I went to System > Preferences > Font  and under Font Rendering, I changed from the default Best Shape to Subpixel Smoothing (LCD) and hit closed.  When I rebooted, I couldn't believe how sharp the fonts look in Swiftweasel and terminal.  

I'm just excited that I finally found the solution to this problem.  Now the desktop dazzles. 

Regards

---

