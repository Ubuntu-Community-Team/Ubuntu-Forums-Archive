---
title: "Compiz &amp; Twinview"
date: 2007-01-10
forum: General Help
---

### Post by invalid on 2007-01-10
I should probably start off by saying this is **not** a question relating to Beryl; this is a Compiz concern. (I know there is an option to solve the problem through Beryl, however I choose to use Compiz for the speed and fluid movement.)

I am having a problem with Compiz, relating to multiple monitors (using nvidia's twinview). When I rotate the cube, it does not act as one large single cube. It displays two cubes (each the same, but rotated 1/2 a turn). This is somewhat hard to explain, so I have attached a screenshot.

Using the desktop zoom plugin, it zooms only on one monitor at a time. The other remains at it's natural size.

In the screenshot, the cube is of size 2. I normally use a cube of size 4 (which results in two octagonal drums), but it is hard to see what is happening in a screenshot.

I can't seem to find any setting with compiz or xorg to stop this behavior. I would like one large cube, as it once was long ago.

Any help or suggestions would be great!

Thanks,
Beau

---

### Post by invalid on 2007-01-13
bump

---

### Post by spd106 on 2007-01-18
Sorry this took so long for a response.
I found that adding this line to the xorg.conf helped on beryl and since installing compiz from gandalfn's repo I haven't had this problem.
```
    Option         "NoTwinViewXineramaInfo" "true"

```

---

### Post by invalid on 2007-01-19
> **spd106 said:**
> Sorry this took so long for a response.
I found that adding this line to the xorg.conf helped on beryl and since installing compiz from gandalfn's repo I haven't had this problem.
```
    Option         "NoTwinViewXineramaInfo" "true"

```

Thanks a lot for the suggestion, however it doesn't quite work for me. This option, at least for me, extends things as one would find with Xinerama rather than Twinview, regardless of what the Xinerama option is set to - and has no change on the cube layout.

I came across someone else with a similar yet disjoint problem, and it pointed me in a close direction. If I change compiz->general->screen0->options->detect_outputs to false, and set compiz->general->screen0->options->outputs to [1280x1024+0+0,1280x1024+1280+1] I at least get a step closer to what I am aiming for. The cube appears as one large rectangle (as it should) when rotating the cube left and right, however now overlaps and or duplicates itself on the top and bottom when they are in view.

I am happy to at least work with this, at least for now. I would still like to hear any suggestions. I also don't know the purpose behind all the values in the outputs key, if anyone might be willing to explain what they all represent.

Thanks
Beau

---

### Post by spd106 on 2007-01-19
That's odd, because I have detect_outputs on and [640x480 +0+], but it works fine on my two 1024x768 screens.

I also have this line in the xorg.conf under "screen" ```
    Option         "MetaModes"  "CRT-0: 1024x768 +0+0, CRT-1: 1024x768 +1024+0; CRT-0: 800x600 +0+0, CRT-1: 800x600 +800+0; CRT-0: 1024x768 +0+0,NULL"

```

---

### Post by invalid on 2007-01-20
Ok, so here's an update.

I managed to get a single wide cube (no duplication or overlapping) by using the suggested NoTwinViewXineramaInfo option, and enabling detect_outputs within compiz. However, I have lost the twinview functionality (distinct screens). It seems to be acting as Xinerama would, stretching windows and panels across both screens.

I tried using similar MetaModes as posted above, but it makes no change. I will continue to play with these to see if I can get anywhere!

Thanks,
Beau

---

### Post by rvdavid on 2007-07-15
sorry to ressurect this post, but have you come up with a solution for this problem?

regards.

---

### Post by emitchlpd on 2007-07-17
I was able to figure this out a few weeks ago. You can see the post here:

[http://ubuntuforums.org/showpost.php?p=2913064&postcount=5]("http://ubuntuforums.org/showpost.php?p=2913064&postcount=5")

---

### Post by rvdavid on 2007-09-14
Just as a follow up, this issue has now been fixed in compiz-fusion for Gutsy Gibbon. 

I've not tested it with any other releases, nor do I know when they implemented the fix, but after not using compiz for a while, due to this issue, I decided to give it another shot. 

I can enable detect outputs and still have one cube. 
Both monitors are treated as different screens you can maximise in one and it will just fill the one screen and not both. 

It works on prerelease Gutsy Gibbon, I'd imagine the same would apply to the current compiz repository. 

regards,

---

### Post by wolf125 on 2008-06-20
I face this problem,butI solved.
Now I can use both TwinView and Compiz's Desktop Cube. 

[http://f.hatena.ne.jp/images/fotolife/w/wolf125/20080621/20080621014618.png](http://f.hatena.ne.jp/images/fotolife/w/wolf125/20080621/20080621014618.png)

What I did is unchecking output detection and setting output manually.(like below)

[http://f.hatena.ne.jp/images/fotolife/w/wolf125/20080620/20080620235553.png](http://f.hatena.ne.jp/images/fotolife/w/wolf125/20080620/20080620235553.png)

And Changing Multi Output Mode.(like below)
[http://f.hatena.ne.jp/images/fotolife/w/wolf125/20080621/20080621014619.png](http://f.hatena.ne.jp/images/fotolife/w/wolf125/20080621/20080621014619.png)

I hope this will help.

regards,

---

