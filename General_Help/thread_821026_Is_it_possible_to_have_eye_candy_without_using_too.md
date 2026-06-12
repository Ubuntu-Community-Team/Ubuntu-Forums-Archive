---
title: "Is it possible to have eye candy without using too much ram?"
date: 2008-06-06
forum: General Help
---

### Post by Sashin on 2008-06-06
I'm running Ubuntu Hardy Heron. I'm using both Compiz-fusion and emerald as my window managers. I have both Screenlets and AWN Running at start up, and am using a four sides inside cube.

Only problem is when I log in I'll have to wait up to 10 seconds for everything to be accessible, and by default it can be using up to 50% of my ram.

When I run Macromedia Flash through Wine, and preview it lags and when I try to render clouds with photoshop it tells me there is not enough Ram. (It didn't happen before)

At the same time I've grown really attached to all the eye candy and desktop effects, is there a way to use it all without using much Ram?

Here is a screenshot of my Desktop.

[http://i27.tinypic.com/2hhhxg7.png](http://i27.tinypic.com/2hhhxg7.png)

I really want it looking as good as that, but still using significantly less ram.

---

### Post by Sashin on 2008-06-06
Can Anyone help? Something that looks good but isn't Ram hungry is all I need...

---

### Post by Sashin on 2008-06-07
Anyone?

---

### Post by easybake on 2008-06-07
Using Compiz Fusion Icon you could switch to Metacity when using more CPU hungry programs.

---

### Post by el-mar01 on 2008-06-07
Nice screenshot ... what font do you use ??

---

### Post by bijeeshvs on 2008-06-07
do one thing 
get rid of the screenlets u use for system monitering and if u need one use "conky" its not a screenlet but its pretty cool........ screenlets eat considerable memmory when there is a lot of them also check ur system moniter to see which program is eating up memory

---

### Post by deepclutch on 2008-06-07
you can try the buggy compositing mode of metacity. use "gconf-editor" and browse to apps>metacity>general>comp. mode

---

### Post by Sashin on 2008-06-07
Thanks, I deleted a few screenlets and it's much better only using up 35% ram at default even with emerald and the cube running. Funny thing is, the screenlets actually use a comparable amount of RAM as photoshop under wine. I still have a few of them though. AWN as well.

I'm using Segoi UI, the Vista font. 
Runs better now and still looks really good.Could still be better I'll try Conky.

Here's a newer screenshot.

[http://i27.tinypic.com/bgsqyc.jpg](http://i27.tinypic.com/bgsqyc.jpg)

---

### Post by Sashin on 2008-06-07
Still takes a while to start up, I suppose that either Compiz-fusion, Emerald or the screenlets.

---

### Post by LaRoza on 2008-06-07
Please use thumbnails or links and don't embed large images.

imageshack.us makes thumbnails for you and gives you the code to use so you just have to copy and paste, very handy.

---

### Post by Happy_Man on 2008-06-07
I second Conky, and also recommend that you get rid of the giant sidebar, as it's probably the most RAM-hungry thing there. Metacity's compositing engine isn't too bad, it can run AWN, but not Emerald, nor does it have very many snazzy effects. It's worth a shot, though.

---

### Post by MattBD on 2008-06-07
One way to get eye candy while maintaining a lightweight system would be to switch from using Gnome to E17 - it's possible to install this in Ubuntu, but a dedicated distro like OpenGEU is probably a better bet.

---

### Post by rainwalker on 2008-06-07
Also, although I'm not sure how effective this would be at freeing up memory, getting rid of either the panel at the top or AWN at the bottom would save some screen real estate (plus, it's kind of redundant to have both).

---

### Post by halln on 2008-06-08
i installed ubuntu on my friends lappy including eye candies (screenlets and awn) but start up is awfull, it took ages for it to load. What i did is, remove awn and use cairo-dock instead. Remove screenlets and use conky, after that booting time became a bit quicker.

---

### Post by bijeeshvs on 2008-06-09
Azureus is also taking considerable amount of ram, i think...............

---

### Post by rainwalker on 2008-06-09
> **bijeeshvs said:**
> Azureus is also taking considerable amount of ram, i think...............

Try Transmission; It's simple but very useful.

---

### Post by klange on 2008-06-09
OP: You need to define "too much RAM". All of my fancy effects (Compiz, Emerald, Cairo-Dock, and Screenlets) combined take only ~100MB of RAM. Cut my overuse of monitoring Screenlets out of the mix and it plummets to ~60MB (Compiz taking only ~20, with a boatload of plugins).

> Metacity's compositing engine isn't too bad, it can run AWN, but not Emerald
It's not that the compositing engine won't run Emerald, it's that Metacity itself is a window decorator, so you can't run another one. I'm sure it's probably possible to code out the decorations from Metacity and then run Emerald, but that probably wouldn't be a good idea.

---

### Post by gameryoshi600 on 2008-06-09
I used to have AWN and screenlets, for me i used alot and they ate up alot of ram. just get rid of some or uninstall awn and screenlets which is what i did. do you have a decent graphics card for compiz, + all the eye candy?

---

### Post by fabounet on 2008-06-10
if you want to save memory/cpu you can use Cairo-Dock for both dock and desktop widgets, it saves you 1 program.

---

