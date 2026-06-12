---
title: "Compiz - awesome, but no minimize effects?"
date: 2008-06-24
forum: General Help
---

### Post by Mecharuva on 2008-06-24
Yes, having Compiz again and knowing how to set up all the awesome effects is, well, awesome.
However, when I minimize, there's no effects.
And there should be.
:confused:
I do have animations enabled, which enables minimize effects.
But they don't happen.  x.x
Any love?

---

### Post by tamoneya on 2008-06-24
you need to enable the animations plugin.  This is located under effect in compizconfig settings manager.  There are many effects that you can choose from under the minimize tab.

---

### Post by Mecharuva on 2008-06-24
Not to be rude, but I stated in my post that Animations was enabled.
:/

---

### Post by tamoneya on 2008-06-24
sorry i missed that.  Go into anamations and go to the minimize tab and make a new animation by hitting the new button.  The you need to make sure to open up the match section by hitting the plus button.  Here you select which types of windows have which effects.  I put "(type=Normal | Dialog | ModalDialog | Unknown)" into mine without the quotes.  This will enable it for most windows.

---

### Post by Mecharuva on 2008-06-24
Alright.  Had that set.
Still not working =[

---

### Post by tamoneya on 2008-06-24
Hmm that is odd.  It seems obvious but in the new dialog have you changed the "minimize effect" menu to something other than "none".  Also is the duration set to something other than 0.

---

### Post by Mecharuva on 2008-06-24
yes, yes.
Still doesn't work.

---

### Post by notlim_hardy on 2008-06-24
Mecharuva, I'm trying to get compiz to work here, what do I do? It's already installed, but I don't know what to do next. Thanks.

---

### Post by tamoneya on 2008-06-24
well now that notlim_hardy mentions installing hardy can you confirm that you have compiz running.  Is it possible you are using something like fusion-icon and you are using fusion as opposed to compiz

notlim_hardy: please dont steer the thread off topic.  If necessary start your own thread.  Ill help you out though anyways:  Compiz is installed by default on hardy.  You just need to change the settings to your liking.  hit "alt-f2" and then type "ccsm"

---

### Post by Mecharuva on 2008-06-24
Options are in System > Preferences.

---

### Post by Mecharuva on 2008-06-25
Sorry about that, I went to sleep.
Anyways, I'm pretty sure Compiz is running, I have all the special effects EXCEPT minimize effects.
And sometimes the other effects just don't work randomly either.  Like once every now and then, for a couple of clicks.

---

### Post by issih on 2008-06-25
Theres a "minimize effect" plugin, make sure that is disabled, as its effect is really not much better than the original metacity one.

Probably not a useful suggestion, but worth checking..

---

### Post by Braedley on 2008-07-04
I am having similar problems with animations in Hardy.  Compiz otherwise seems to be working (although I noticed some minor bugs with regards to enabling plugins, but that's not the concern here) as I have a working cube, as well as other plugins working.  My settings as far as the animations are concerned are identical to my Gutsy settings, which would burn a window during close and beam up during minimize, but nothing of the sort happens any more.  I've tried disabling and then re-enabling the plugin, changing the window matching rules, all to no avail.  I know window matching is working, because Pidgin and Exaile are properly moved to the widget layer.

Any other help would be greatly appreciated.
Braedley

---

### Post by eggdeng on 2008-08-10
The missing minimize effect can be recovered as follows.
Right click on the (bottom) panel, choose Add to panel. Choose Window List and click Add.
Windows will now minimize to the Window List using the appropriate effect. :)

---

### Post by overdrank on 2008-08-10
Moved to Desktop Effects & Customization :)

---

### Post by 4Play on 2008-08-14
> **eggdeng said:**
> The missing minimize effect can be recovered as follows.
Right click on the (bottom) panel, choose Add to panel. Choose Window List and click Add.
Windows will now minimize to the Window List using the appropriate effect. :)

I have the same problem, everything works except for the minimize effect. The solution mentioned above did not work for me...

I am running ubuntu hardy, on a XPS M1530, I managed to get the minimize effect going once, I think changing the profile in the Simple CCSM, (I am now with the "Holywood got Nothing" profile..however, since all the simple editor does is edit the advance one for you, and I am adding the effects on the advance editor, I don't see why the minimize effect doest work...

Thanks

update: I now found out the "window focus" effect also does not work...the only effects that DO work are the open and close effects...the solution to this must be simple...

---

### Post by Zoshonel on 2008-09-02
Under animations select "Minimize Animation" tab, then click the edit button, instead of "Zoom" select "Random" and close... I hope this helps... 
By the way, sorry for my bad english...

---

### Post by stat30fbliss on 2008-09-03
This seems to be a common issue lately.  I am also experiencing the issue, and have been scouring the forums for posts with people experiencing it as well.  It seems very few people have an in depth idea of what is causing the sudden stop in the minimize effects. 

Maybe we should contact compiz with the issue and see what they say?  Anyone have a link to their feedback/troubleshoot page, maybe a FAQ?

---

### Post by sayakb on 2008-09-03
Try restoring the compiz settings to default. In CCSM, click **Preferences** and click **Restore to Defaults**.

---

### Post by rsannie on 2009-08-23
I was having the same problem.  Make sure "Enable Animations" is checked on the left hand side.  Under animations, click minimize animation tab, inside minimize effect, double click the first line (default is zoom?), change the minimize effect to whatever you wish (random, magic lamp, etc), then click close.

---

### Post by michaelwu on 2009-08-25
Hi, im a brand new Ubuntu user and i am experiencing a similar problem. I have Jaunty installed and i managed to get the rotating cube working. Wobbly windows have been working from the start. For some reason none of the animations(open close minimize) are not working. I've tried many of the suggesttions mentioned in this thead.

Some help would be greatly appreciated :D

---

### Post by darco on 2009-08-25
My Compiz Bible:

[http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/entries/2007/8/29/How-to-set-up-Compiz-Fusion)

I love the random effects on open/close or minimize

darco

---

