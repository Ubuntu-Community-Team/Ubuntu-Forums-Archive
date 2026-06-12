---
title: "Images in Beryl"
date: 2006-12-13
forum: General Help
---

### Post by maniacmusician on 2006-12-13
Hey,

After today's svn update of beryl, the top and bottom images on my cube have dissapeared. Also, today, I tried to set my own image as the skydome, but it won't display. Any suggestions?

thanks.

---

### Post by hikaricore on 2006-12-13
There should be a plugin named Png (png image loader).  Enable that and you should be good to go.
I thought that T broke the snow plugin until I noticed new plugins in the menu.

There's also SVG (svg image loader) incase you're using anything of that type.

---

### Post by maniacmusician on 2006-12-13
awesome, thank you. The snow plugin is pretty neat, but i usually have it off :) I'm actually trying to use beryl to be productive instead of just taking up RAM and whatnot. Which is why I have 2 profiles; one for showing off, one for everyday use. I have to say, some of Beryl's tools actually do help me be more efficient. Thanks again :)

edit: just out of curiosity, is there any way to make the top and bottom images more opaque than the rest when using transparent cube?

---

### Post by d3v1ant_0n3 on 2006-12-13
Gah! I'd noticed the lack of cubecaps and skydome, and just figured it was one of those bumps that hits beryl every so often. I was going to be patient and wait for it to all work again.

Thanks for pointing me in the right direction:KS

---

### Post by hikaricore on 2006-12-13
Hehehe Ubuntu the great timewaster and base of useless knowledge.

---

### Post by maniacmusician on 2006-12-13
lol. So, do you know if I can set opacity for the cubecaps seperately from the workspaces or is this just impossible?

@d3v1ant_0n3 : how does beryl run on that laptop? doesn't seem like it would have a lot of manpower.

---

### Post by d3v1ant_0n3 on 2006-12-13
It's pretty smooth actually- no blurfx or water, and things get sluggish if I use xglsnow. 

I use a fairly stripped animation set (zoom and fade, with magic lamp for minimize)- the bling ones look great, but fire is slllooooow. Beamup works good tho.

I have some problems watching movies in beryl (lotsa wierd tearing) but that's just a click into metacity away- I tend to watch movies fullscreen anyway, so I don;t need the other cube faces:D 

If anything, I think I find Ubuntu smoother with beryl on rather than off.

---

### Post by hikaricore on 2006-12-13
I don't think it's possible yet... tho I havn't tried png transparency via the alpha layer.  I would assume it would work considering beryl can properly display other pngs with transparency (Ex. xglsnow).  Might want to try that route.

d3v's laptop isn't far off from my box's specs:

Ubuntu Edgy
Kernel 2.6.17-10-386
Beryl 0.1.3 SVN
Intel(R) Celeron(R) CPU 2.70GHz
512Mb (unknown speed)
Intel 845G chipset (82845g/gl)

And mine runs decently enough, snow is what really kills me hehe.  But rotation, transparency, and fire work perfectly for me.

---

### Post by hikaricore on 2006-12-13
Water isn't supported by my particular card/driver spits out;

beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing

Which from what I understand has to do with pixel shaders.

d3v try changing your fire settings to:

Number of fire particles: 500
Fire particle size: 3.5
Fire particle slowdown: 0.7
Fire particle life: 0.6

I also have fire direction set as UP.

And Fire constant speed and fire smoke checked in the Animations config.

---

### Post by d3v1ant_0n3 on 2006-12-13
> **hikaricore said:**
> Water isn't supported by my particular card/driver spits out;

beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing
beryl: water: GL_ARB_fragment_program is missing

Which from what I understand has to do with pixel shaders.

d3v try changing your fire settings to:

Number of fire particles: 500
Fire particle size: 3.5
Fire particle slowdown: 0.7
Fire particle life: 0.6

I also have fire direction set as UP.

And Fire constant speed and fire smoke checked in the Animations config.

I really like those settings8)  Thanks.

Apparently the intel chipsets DO have pixel shaders but aren't supported in linux' drivers or something similar- there was a thread kicking around somewhere in beryl forums that explained it much better than I can.

---

### Post by hikaricore on 2006-12-13
> **d3v1ant_0n3 said:**
> I really like those settings8)  Thanks.

Np, once again way too much free time doing nothing and making my desktop pretty.

> **d3v1ant_0n3 said:**
> 
Apparently the intel chipsets DO have pixel shaders but aren't supported in linux' drivers or something similar- there was a thread kicking around somewhere in beryl forums that explained it much better than I can.

Yea, I really wish intel would still "support" the driver updates that died with them years ago, this probably explains why the outside ground textures look like baby vomit when I play WoW.  Endless miles of missed textures and tearing due to lacking support for simple video functions.  *sigh*  I can still instance farm tho.  hehe

---

### Post by maniacmusician on 2006-12-13
> **hikaricore said:**
> I don't think it's possible yet... tho I havn't tried png transparency via the alpha layer.  I would assume it would work considering beryl can properly display other pngs with transparency (Ex. xglsnow).  Might want to try that route.

d3v's laptop isn't far off from my box's specs:

Ubuntu Edgy
Kernel 2.6.17-10-386
Beryl 0.1.3 SVN
Intel(R) Celeron(R) CPU 2.70GHz
512Mb (unknown speed)
Intel 845G chipset (82845g/gl)

And mine runs decently enough, snow is what really kills me hehe.  But rotation, transparency, and fire work perfectly for me.
I don't really think that will work...I want the cubecaps to be **more** solid than the rest, not less. Oh well, just a little thing. I'm pretty happy with the rest of it. :)

---

