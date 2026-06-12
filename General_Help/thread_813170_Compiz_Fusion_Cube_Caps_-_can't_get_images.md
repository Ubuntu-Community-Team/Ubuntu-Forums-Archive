---
title: "Compiz Fusion Cube Caps - can't get images"
date: 2008-05-30
forum: General Help
---

### Post by montgoja on 2008-05-30
I've been sifting through the forum looking for a thread that handles my issue, but no luck.  I know from my searching that this is a pretty frequently handled issue, but mine is... unique?

I just did a clean install of Hardy Heron a few weeks ago, and one of the most satisfying results of this clean install is a new compatibility for Compiz Fusion - my ATI Sapphire card gives me a lot of headaches, but each new release of Ubuntu is making a lot of progress.

I've gotten practically everything on Compiz to work for me that I've ever wanted to have work (I could never get -anything- to work in Compiz before Hardy.  Not even wobbly windows!) except for an issue I'm having with my cube caps.

I've got the Cube Caps plugin enabled and have tried using the default cubecap images on the plugin, cubecap images from compiz-themes.org, and pictures from my own pictures folders.  None of these images are showing up on the caps when I rotate the cube.  It's just plain white.  I have JPEG, Png, Svg, and Text plugins enabled, but nothing's showing.

If I use the single cube cap option, I can get any picture I want to display, provided I have Cube Caps disabled in the utility options.  But that only gives me one cap and I'd like to have two different ones.

Any ideas?  ](*,)

---

### Post by caro on 2008-05-30
I haven't heard of this before, so all I have are some guesses....you may have already checked these; if so, didn't mean to waste your time.

On the Cube Caps plugin setting, under the Behavior tab, do you have Draw Top Face and Draw Bottom Face enabled?

Are pictures you want to used sized correctly (i.e. not larger than your system can handle?)

Good luck.

---

### Post by montgoja on 2008-05-31
I have all of the boxes checked under Behavior, and the only pictures I have set in the box right now are the defaults (fusioncap.png on top and compizcap.png on the bottom) that compiz sets natively.  I tried editing the filepath on the selection box to include the full path of the default .png files (instead of just fusioncap.png I tried /usr/share/compiz/fusioncap.png) but that had no effect, either.  I'm thinking a 600X600 cap image shouldn't be an issue when my computer's resolution is currently set at 2560 x 1024 (I run a dual monitor setup).  I'm including screenshots if they'll be of help.

---

### Post by Ty61690 on 2008-05-31
Ok i am having a problem with the bottom face. I can get the image to display on all four sides of the cube and the top. But not the bottom. Anyone know anything?

---

### Post by caro on 2008-05-31
What are your settings on the Desktop Cube plugin under the Appearance tab?

---

### Post by montgoja on 2008-06-11
Ty -
There are two different settings options in the Settings Manager (CCsM) that manage the cube.  One is in the actual  Desktop Cube option in the Desktop section.  In the Utility section (I've yet to hear a reasonable explanation why it's in Utility, but whatever) there is another option you need to select.  It is called Cube Caps and is near the top of the list.  If you go into the options for this section, you should have three tabs on top:  General, Appearance, and Behavior.  Of course, be sure to enable Cube Caps first by checking it in the CCsM (either on the main menu or in the options menu by checking the box on the left).  Under the Appearance tab, you have the options to set cube colors and images.  Under Behavior, you can select the way in which the images will be rendered (naturally, if you want images on the caps, you should select draw top face and draw bottom face) and how they will be scaled, treated, etc.

It is strange that this whole option isn't simply included in the Desktop Cube settings in the first place, but I hope that helps.  My computer still won't render the images after I select all the options and do everything else I can think of, so I have the option of either solid colors or a single image on the top.  Oh well.  It's still cool.  haha.  Hope that helps!

---

### Post by keinea on 2008-08-18
Reference to: montgoja

" ...  My computer still won't render the images after I select all the options and do everything else I can think of, so I have the option of either solid colors or a single image on the top. Oh well. It's still cool. haha. Hope that helps!"


I don't know if this will help, but I was having a problem setting up the SkyDome feature using the Settings Manager (CCsM), and it was suggusted from an earlier forum topic to use the 'gconf-editor' instead of the Compiz Manager.  At the command line simply enter 'gconf-editor'.  I found this utility so useful that I've added it to my menu list.

Cheers,
Keith
8-)

---

### Post by Kinetic_lord on 2008-09-03
i can't even see the cube caps... i only see the sides... can u help? :(

---

### Post by sayakb on 2008-09-03
Sorry, haven't read the whole thread...
First of all, **check** the Cube Caps plugin (or the Deformations plugin, if any).
Add an image that is smaller then the largest image size that could be handled by the graphics card. For example, try adding a 500x500 image to test.
If none work, see my post in the Great desktop effects FAQs, page 3 on howto install compiz 0.7.6 and there, set the cube caps within the Cube Deformation plugin.

---

### Post by BlackLLama on 2008-09-03
when spinning the cube hit space

---

### Post by Staesys on 2009-03-09
This is old I know, but I just found the answer myself. I hope this helps someone.

[http://thegeekylife.blogspot.com/2008/11/setting-up-desktop-cube-in-ubuntu-810.html](http://thegeekylife.blogspot.com/2008/11/setting-up-desktop-cube-in-ubuntu-810.html)

---

### Post by vijaym on 2009-03-11
Hey thanks
that link helped.

---

### Post by erikengstrom19 on 2010-08-31
I have everything checked that i need to and my cube worked perfectly last time i used it, but after i turned it off and restarted it the next day my skydome image is not appearing and neither are my top and bottom cap images. Any help?!

---

