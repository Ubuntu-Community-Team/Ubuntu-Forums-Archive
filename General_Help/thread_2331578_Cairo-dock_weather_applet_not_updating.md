---
title: "Cairo-dock weather applet not updating"
date: 2016-07-23
forum: General Help
---

### Post by bookie2 on 2016-07-23
Hi guys!
I have Trusty 14.04 lts xfce.
Up and till a couple of months back I had a cairo-dock weather applet that worked....but now I just have a useless icon...;)
I have looked at different threads but there is always information lacking....?
 
Does anyone have a fix for this?
bookie

---

### Post by QDR06VV9 on 2016-07-23
I use Docky...but have had the same as you report..useless icon.
What I did was clean the configuration from that location that I wanted my weather from..and closed Docky and then re-added the same location..now works like a charm again.
Hope the same for you.

---

### Post by bookie2 on 2016-07-23
Hi runrickus!
No, I have tried that...I even tried the reply at the bottom of this [thread]("http://askubuntu.com/questions/774438/cairo-dock-weather-applet-not-working") but that doesn't work at all.
If I add the file recommended...don't even get a useless weather icon....and no choice to add one either....?
bookie

---

### Post by QDR06VV9 on 2016-07-23
> **bookie2 said:**
> Hi runrickus!
No, I have tried that...I even tried the reply at the bottom of this [thread]("http://askubuntu.com/questions/774438/cairo-dock-weather-applet-not-working") but that doesn't work at all.
If I add the file recommended...don't even get a useless weather icon....and no choice to add one either....?
bookie
I hope you are understanding Docky is a dock application like cairo-dock..I'm not sure I follow on your reply.."tried the reply at the bottom of this [thread]("http://askubuntu.com/questions/774438/cairo-dock-weather-applet-not-working") but that doesn't work at all."
Well the only thing I can add here then is to uninstall Cairo-Dock and removing anything left in your home directory..Look in ~/.cache and look in ~/.config and see if there is a reference to cairo-dock there and remove them all.
Then reinstall cairo-dock.
Fingers Crossed

---

### Post by bookie2 on 2016-07-23
Hi again!
Sorry, if you look at this solution to the problem according to the person that submitted it....
> 

[COLOR=#111111][FONT=Ubuntu]I fixed weather plug-in on Kubuntu 14.04!!![/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]-remove all cairo-dock from Synaptic, and install cairo-dock-[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo add-apt-repository ppa:cairo-dock-team/ppa[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt-get update[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]sudo apt-get install cairo-dock cairo-dock-plug-ins[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Then from [https://drive.google.com/open?id=0B-XSYP5W-8Wea2NWTGJtSkxybEk](https://drive.google.com/open?id=0B-XSYP5W-8Wea2NWTGJtSkxybEk)[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]i copied the file as root in /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-weather.so[/FONT][/COLOR]
And Cairo-Dock weather applet working!!!


I followed the instructions and removed cairo-dock....and then reinstalled it again...

BTW...i do know about Docky...;)

bookie

---

### Post by QDR06VV9 on 2016-07-23
Sorry My Bad... that was a link to what you have tried,,,,sorry more coffee needed:)
So by the looks of it you will have to download that file provided in that page:[https://drive.google.com/open?id=0B-XSYP5W-8Wea2NWTGJtSkxybEk](https://drive.google.com/open?id=0B-XSYP5W-8Wea2NWTGJtSkxybEk)
And move it to < /usr/lib/x86_64-linux-gnu/cairo-dock/libcd-weather.so > As Root

---

### Post by QDR06VV9 on 2016-07-23
> **bookie2 said:**
> Hi again!
Sorry, if you look at this solution to the problem according to the person that submitted it....


I followed the instructions and removed cairo-dock....and then reinstalled it again...

BTW...i do know about Docky...;)

bookie
Yes I saw that but I also seen where it was_** voted down **_so try the method I have shown in my previous post:)

---

### Post by bookie2 on 2016-07-23
Hi again!
Well, that is what I have already tried.....I reinstalled cairo-dock and used the libcd-weather.so but I lose my weather icon totally and there is no choice to add the weather icon after replacing the old libcd-weather.so with the new one....
Sorry, if I wasn't making myself clear....old age and a "Man's Cold" ...;)

bookie


[COLOR=#FFFFFF][FONT=arial]Slibcd-weather.so[/FONT][/COLOR][COLOR=#FFFFFF][FONT=arial]libcd-weather.so[/FONT][/COLOR]

---

### Post by QDR06VV9 on 2016-07-23
> Sorry, if I wasn't making myself clear....old age and a "Man's Cold" ...:wink:

Hey No worries:) I failed to realize that you had a link to what you needed assistance for. But now I think we are both on the same page now:wink:
Give me a little time to see if I can come up with something for you here...I will report back.
Kind Regards

---

### Post by QDR06VV9 on 2016-07-23
This seems to be that the project is not getting any love by the Devs..as it now shows the last work was reported [B]"cairo-dock 63 weeks ago
Successfully built" [/B]
And I have been unsuccessful with the patch mentioned on Ask Ubuntu and the one mentioned on there forums here:[http://www.glx-dock.org/bg_search.php](http://www.glx-dock.org/bg_search.php)
With a lot of users saying the same as you.
Their PPA is here but seems to be at a stand Still ATM:[https://launchpad.net/~cairo-dock-team/+archive/ubuntu/ppa](https://launchpad.net/~cairo-dock-team/+archive/ubuntu/ppa)
So I am clueless on how to advise you now.
But for the record Docky weather work a treat.
Sorry I did not have better news for you.
Kind Regards

---

### Post by bookie2 on 2016-07-23
Hi again!
Fantastic help even if it doesn't solve the problem....this is what I love about Linux!!
I am very pleased to know someone that goes out of his way....like so many...to try and help others...
Not just got a Man's Cold...trying to come to terms with reaching 60 next week 28th July....Help!!
I can take a look at Docky...was a while ago...
Have you some good links, info that will get me on my way?

Thanks again for your time and enthusiasm!!

bookie

---

### Post by QDR06VV9 on 2016-07-23
Thank you for the kind reply..and I know how you feel @ 63 years young here.
You can install it by
```
sudo apt install docky
```
And add the weather by clicking on the Anchor Icon and look at the tabs at the top and click on Dockets and add the weather docket and enter your zip code or city.
You may have to wait for the dockets to populate or close and click the Anchor Icon twice to see the Dockets come to view.
Info for Docky here: [https://apps.ubuntu.com/cat/applications/oneiric/docky/](https://apps.ubuntu.com/cat/applications/oneiric/docky/)
Take Care of that Cold and Kind Regards

---

### Post by bookie2 on 2016-07-24
Hi runrickus:)

I thank you for all your help!
I am going to remove cairo-dock and install Docky....;)

bookie

---

