---
title: "laptop ubuntu overheating"
date: 2013-07-30
forum: General Help
---

### Post by YWCyeXG on 2013-07-30
My laptop has been overheating lately like no other.   Sensors are at like 150 F.  I'm used to my HP Pavilion having heating issues.  Sometimes I restart my laptop and whatever process that was causing it to overheat disappears.  Now it begins to overheat right as I start my laptop up.  The only changes recently that I've made are switching to firefox and using a Vizio external display.  Not sure if any of those two factors would require much resoruces tough as opposed to a single laptop screen and google chrome.  Monitor is [http://store.vizio.com/e221a1.html](http://store.vizio.com/e221a1.html)

---

### Post by YWCyeXG on 2013-07-30
post edited

---

### Post by Feathers McGraw on 2013-10-19
It's probably an issue with your graphics cards.

I wrote a tutorial for this after I had an overheating problem with my HP Pavilion DV6 3122-sa. You can find it here:

[http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/](http://www.samhobbs.co.uk/2013/09/ubuntu-linux-hp-pavilion-dv6-overheating-dual-amd-graphics/)

It may be useful to you if you have an AMD processor and AMD/ATI graphics card.

If you can post your laptop's specs we can probably help narrow things down - the tutorial may not be relevant to you if you have certain hardware.

Feathers

---

### Post by princeofnam on 2013-10-19
I have the HP pavilion g7-1070us. apparently the graphics card is the chipset variety "Intel HD Graphics"  I guess this doesn't apply to your post.  Thanks though

---

### Post by Feathers McGraw on 2013-10-19
Yep you're right, my post was written with something else in mind.

I [found the specs for your laptop here]("http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/kb/docDisplay/?spf_p.tpst=kbDocDisplay&spf_p.prp_kbDocDisplay=wsrp-navigationalState%3DdocId%253Demr_na-c02729693-1%257CdocLocale%253D%257CcalledBy%253D&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken"), have included them in case they're useful for anyone else coming to the thread.

Looks like you have integrated Intel graphics (as you said) and no discrete graphics card. I've installed Kubuntu on about 5 laptops with similar specs and haven't had any problems so far!

To be honest, 150*F isn't all that hot (about 65*C). Not ideal, and you should keep an eye on it, but only start worrying when it reaches 75*C-80*C.

In the meantime, you may notice some improvement if you clean the laptop of dust using a can of compressed air. The cans are really cheap , and doing this is another thing that took my temperature down by 20*C.

If you choose to try this, angle the can up into the laptop instead of down, the air that comes out will be much drier.

Feathers

---

### Post by princeofnam on 2013-10-19
unfortunately I tried this by opening up the laptop itself.  the fan itself was pretty clean.  i couldn't take the entire mobo out though so there could have been a component to the CPU that was attracting dust.

---

### Post by Feathers McGraw on 2013-10-19
That's strange.

You mentioned sensors were at 150F, which sensors were they?

Feathers

---

### Post by princeofnam on 2013-10-19
Not sure honestly.  These sensors were part of a default Kubuntu applet.  Is there a way to tell?

---

### Post by Feathers McGraw on 2013-10-19
Try installing psensor?

---

### Post by princeofnam on 2013-10-31
Hey! Sorry for not responding in awhile.  I've been away from home and not able to tend to my laptop.   I installed psensor and attached the values shown with it.    Seems pretty high.  Or is it??

---

### Post by Feathers McGraw on 2013-10-31
Yeah, they're pretty high. If I were you I'd keep looking for a way to bring the temp down, but unfortunately I'm out of ideas!

:confused:

---

### Post by Mopar1973Man on 2013-10-31
I would dart over to terminal and fire up "top" and take a peek at what is running. A better program that allow a bit more is "htop".  Look for apps using large amount of resources.

---

### Post by TusharG on 2013-10-31
I've HP Pavilion dv6 laptop and for last 2 years I'm facing the over heating issue only in Ubuntu and its varients. On the same laptop with Windows 7 everything just works fine! Can you share your hard disk temperature as well? use hddtemp /dev/sda command... replace sda with your correct dirve location. 
    I've tried various solution and I have found a workaround to it but before that please share your disk temerature, specially plug in the power connector and then observe the disk temerature every 5 min and then share the disk temerature.

---

### Post by princeofnam on 2013-11-02
i checked top and it's as suspected, Firefox is responsible for 50% of my CPU usage.  and it's usually with flash.  i've noticed firefox is considerably worse than chrome on my laptop but I find this hard to believe seeing as how long firefox has been released and its default status with ubuntu's distro.  

Also I tried to run hddtemp and i got this sadly

> xx:~$ sudo hddtemp /dev/sda
[sudo] password for xx: 
WARNING: Drive /dev/sda doesn't seem to have a temperature sensor.
WARNING: This doesn't mean it hasn't got one.
WARNING: If you are sure it has one, please contact me (hddtemp@guzu.net).
WARNING: See --help, --debug and --drivebase options.
/dev/sda: Hitachi HTS545050B9A300:  no sensor



---

### Post by Petro Dawg on 2013-11-02
Sometimes you just have to get desperate.
 
I battled for long time to control the temps until I just got serious about it...

[http://ubuntuforums.org/showthread.php?t=2045798&page=6#55](http://ubuntuforums.org/showthread.php?t=2045798&page=6#55)

It seems Linux just doesn't play well with some laptops.

---

### Post by princeofnam on 2013-11-02
haha that's awesome.  thing is i experience this with windows and ubuntu so i think it's a hardware issue honestly.  i tried to open up my laptop but the last step of removing the motherboard was the hardest of all

---

