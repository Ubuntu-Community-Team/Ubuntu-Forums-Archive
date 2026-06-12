---
title: "GNOME Customisation - Emerald/GTK/GDesklets"
date: 2008-05-30
forum: General Help
---

### Post by ChildOfMana on 2008-05-30
I'm running Hardy and trying to customise my desktop. Got a few queries if anyone can help though.

Firstly, does anyone know of a place I can get _matching_ GTK and Emerald themes? gnome-look.org doesn't have very many matching themes and I'm finding it very difficult to marry up GTK and Emerald themes to make my desktop look pretty. I'm useless at making my own themes too :(

Also a couple of quick question about GDesklets (as [www.gdesklets.de](www.gdesklets.de) is far from useful in this regard right now!):

How do I make GDesklets run on start up? And does anyone know how to configure the GoodWeather desklet to actually display any info? I live in the UK and am trying to get it to display the weather report for Liverpool. I think I've entered the right location code (as per weather.com) but all the desklet will display is "N/A loading..."

Thanks.

---

### Post by EXCiD3 on 2008-05-31
For inspiring matching themes check out everyone else's here: [http://ubuntuforums.org/showthread.php?t=776915](http://ubuntuforums.org/showthread.php?t=776915)

You can have gdesklets autorun by going to System > Preferences > Sessions and adding a new entry for gdesklets. This is a list of the applications that are autorun when you login.

And if i looked it up correctly the location code for Liverpool should be: UKXX0083

I have never been a fan of gdesklets and I recommend you check out conky instead. You can configure it to check the weather too, mine also checks email and displays the currently playing song. Here's a screenshot of my desktop with conky (on the right, prints directly to the desktop): _[http://www.flickr.com/photos/20473873@N03/2474068143/sizes/l/](http://www.flickr.com/photos/20473873@N03/2474068143/sizes/l/)_

---

### Post by ChildOfMana on 2008-05-31
Thanks man.

Yeah that's the area code I'm using but no joy. No matter though.


I'll give conky a try - loving the look of that desktop.

Appreciated.

---

### Post by jjgomera on 2008-05-31
or if you want more weather info: [http://ubuntuforums.org/showthread.php?t=760527](http://ubuntuforums.org/showthread.php?t=760527)

so i have it:

[img]http://ubuntuforums.org/attachment.php?attachmentid=72230&d=1212180317[/img]

---

### Post by issih on 2008-05-31
Worth checking out screenlets too...like gdesklets, but imho prettier. Screenlets also integrate easily with the compiz widget layer plugin to give a mac dashboard effect.

---

### Post by EXCiD3 on 2008-05-31
> **ChildOfMana said:**
> Thanks man.

Yeah that's the area code I'm using but no joy. No matter though.


I'll give conky a try - loving the look of that desktop.

Appreciated.

I'm not sure why the weather wont work for you...if i wasnt on dialup and using my parents comp i would try it and see what results i got. Maybe someone else can try and see what they get.

As for conky weather, i was just using a really OLD script to check weather that doesnt show you much. As mentioned earlier (with a beautiful screenshot i might add ;)) the new conky weather script looks gorgeous and I cant wait to get some time to set it up myself! :) Its a lot more complicated, but the end result looks amazing!

---

### Post by mikey.duhhh on 2008-06-01
I installed Emerald and now I have no visible close, maximize, unmaximize icons nor a visible bar on top.  I then installed the Compiz Fusion Icon  and tried turning off Emerald.  That merely sent me back to no cube and two desktops but I did get back the top bar.  I played around with Emerald, tried various settings, but nothing worked properly.  I then opened synaptic and removed Emerald and the associated package, but still kept the CF Icon.  Same result.  I need the top bar visible.  

Help!

---

### Post by EXCiD3 on 2008-06-01
> **mikey.duhhh said:**
> I installed Emerald and now I have no visible close, maximize, unmaximize icons nor a visible bar on top.  I then installed the Compiz Fusion Icon  and tried turning off Emerald.  That merely sent me back to no cube and two desktops but I did get back the top bar.  I played around with Emerald, tried various settings, but nothing worked properly.  I then opened synaptic and removed Emerald and the associated package, but still kept the CF Icon.  Same result.  I need the top bar visible.  

Help!

So are you saying you have compiz working just no titlebars or is it a different problem?

Try using "metacity --replace" in the Alt-F2 run box. Setting the window decorator to metacity in fusion-icon should do the same thing.

If this isnt the case, can you include a screenshot?

---

### Post by ChildOfMana on 2008-06-01
I've tried conky, screenlets and GDesklets but having pretty much the same problem with all of them (can't load the weather data).

I'm just wondering if it's something to do with my iptables config (I recently installed and ran lokkit) or maybe my router (do I need to forward a particular port)?

---

### Post by ChildOfMana on 2008-06-01
Eureka!

[http://ubuntuforums.org/showthread.php?t=784053](http://ubuntuforums.org/showthread.php?t=784053)

The above thread should help you solve any problems you're having with either GDesklets or Screenlets.

Not sure about conky though.

The problem is basically something to do with weather.com changing their code. You have to find the WeatherScreenlet.py file (mine was in ~/.screenlets/clearweather) and edit it.

All the information's in the above thread if you wade through the posts.

Thanks to james9876 for bringing this to my attention.

---

### Post by ChildOfMana on 2008-06-01
Oh, and mikey.duhhh I had the same problem you have below...

> I installed Emerald and now I have no visible close, maximize, unmaximize icons nor a visible bar on top. I then installed the Compiz Fusion Icon and tried turning off Emerald. That merely sent me back to no cube and two desktops but I did get back the top bar. I played around with Emerald, tried various settings, but nothing worked properly. I then opened synaptic and removed Emerald and the associated package, but still kept the CF Icon. Same result. I need the top bar visible.

Help!

I fixed it by going to System > Preferences > Sessions, clicking Add and entering > emerald --replace in the "command" box. This makes sure emerald loads on start up and draws some pretty window borders for you :)

Hope it helps.

---

### Post by EXCiD3 on 2008-06-01
Yeah thats what i was assuming was going on, but if you have fusion-icon setup to use emerald, it *should* use emerald every time and should also automatically replace metacity with it.

---

### Post by ChildOfMana on 2008-06-02
Yes it *should* but mine wasn't for some reason. Emerald would start but then for some unfathomable reason it'd revert straight back to Metacity again - leaving me with no title bar :( Had to use the Fusion icon to manually change back to Emerald again.

Adding 'emerald --replace' to sessions seemed to fix it though. Working fine so far (fingers crossed!) :)

---

### Post by EXCiD3 on 2008-06-02
I just installed emerald and am using fusion-icon to start emerald for me on login. I will try it for a while and see if it loads emerald correctly or not upon login. I remember a while back emerald would have lots of issues starting but i was hoping it was fixed now. We shall see.

---

### Post by mikey.duhhh on 2008-06-09
> **EXCiD3 said:**
> So are you saying you have compiz working just no titlebars or is it a different problem?

Try using "metacity --replace" in the Alt-F2 run box. Setting the window decorator to metacity in fusion-icon should do the same thing.

If this isnt the case, can you include a screenshot?

Yes, compiz works just fine.

 metacity --replace turns off the cube, and all of compiz-fusion as well.

Now to reboot with emerald enabled again.

---

### Post by mikey.duhhh on 2008-06-09
> **ChildOfMana said:**
> Oh, and mikey.duhhh I had the same problem you have below...



I fixed it by going to System > Preferences > Sessions, clicking Add and entering  in the "command" box. This makes sure emerald loads on start up and draws some pretty window borders for you :)

Hope it helps.


Tried it and it doesn't help.

That's about it.  Almost time to abandon emerald altogether.

---

### Post by EXCiD3 on 2008-06-09
I actually prefer compz *without* emerald. try purging your emerald install and then using fusion-icon.

---

