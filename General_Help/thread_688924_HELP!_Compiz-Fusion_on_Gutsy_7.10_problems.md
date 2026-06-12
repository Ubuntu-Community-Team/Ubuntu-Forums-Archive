---
title: "HELP! Compiz-Fusion on Gutsy 7.10 problems"
date: 2008-02-05
forum: General Help
---

### Post by jgodfrey0723 on 2008-02-05
Hi all I'm completely stumped,

  I've tried searching the forums so please don't flame me but here it goes..

I just installed gutsy 7.10 three days ago (i'm a newb) and have been tinkering with the desktop.  I figured out how to get the Advanced Desktop Effects Manager unlocked and made my desktop perfect.  Well three times now I'll install Kiba-Dock using different methods and it seems like everytime  I do my Compiz settings get messed up. For instance, where Advanced Desktop was is replaced with CompizConfig Settings Manager and it won't open.  I don't even have windows borders.  My theory is that when I install Kiba it says I have updates to install. Everytime I install them the same thing happens (I've reformatted twice.)  Is there a fix so that I dont have to reformat again and lose everything?  When I go to terminal and type ccsm I get the following message:  

Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'

And help for a newb would seriously be appreciated, even if you can point me in the right direction to fix it.  I'm not a computer programmer or that familiar with terminal though so bear with me.  Thanks!!!:)

---

### Post by brijeshchauhan on 2008-02-06
I am also having the same problem.

My ubuntu 7.10 was working fine on my with all the graphics of Compiz fusion. I installed Kiba-doc last night and it messed up compiz fusion.

1) Before installing Kiba-dock the graphics properties was under Settings>Preferences>Advance Graphics Effects. 

But after installing kiba-dock its under Settings>Preferences>Compiz-fusion properties. 

2) The graphics properties are set with default state. Like I have only 2 desktops now and I don't have any compiz-fusion graphics enabled. I am not able to open the properties also, so I cant set it to the earlier state.

Is there any way to get my earlier graphics properties back?

Thanks in advance.

---

### Post by upthelum on 2008-02-06
Maybe start with posting your hardware info. I got a new mobo expecting to run Compiz only to find out i needed pci graphics. It installed ok but it wouldn't do anything

---

### Post by jgodfrey0723 on 2008-02-06
Well I figured it out.  I ended up adding some repositories for fiesty when I have gutsy, and I was downloading compiz for the wrong distro I guess.  Still a newb with linux but it seemed to fix my problem.

---

### Post by brijeshchauhan on 2008-02-06
Can you please write it in detail. Which repos have you installed. I have the same problem and want to get a solution.

thanks in advance

---

### Post by brijeshchauhan on 2008-02-06
I re-installed compiz-preference-manager package and its working back again:guitar:

But I lost all my previous settings. Is there any way to get it back to the earlier settings?

---

### Post by drs305 on 2008-02-06
You can save/export your compiz (advanced desktop) preferences: System, Preferences, Advanced Desktop Effects Settings. Double click Preferences, Export, enter filename.profile to a backup file. It doesn't save everything but at least retains which desktop effects you have enabled/checked. 

If someone knows the files that actually store the desktop settings I'd like to know which ones they are (number of workspaces, window dimensions, etc).

---

### Post by jgodfrey0723 on 2008-02-06
I used some repo's from Trevino's link.  Under the sources.list it was labeled as fiesty eye candy or something.  If you post your repo list I can tell you what it was.

---

