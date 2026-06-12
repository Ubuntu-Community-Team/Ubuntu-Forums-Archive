---
title: "Thunderbird 2 Moztray biff?"
date: 2007-04-20
forum: General Help
---

### Post by kolinab on 2007-04-20
Hi,

I guess maybe it's a little early to expect the dust to have settled from the releases of Feisty and Thunderbird 2 all within 24 hours of each other. I KNEW that would happen.

Anyway, I used the script [here]("https://help.ubuntu.com/community/ThunderbirdNewVersion") to install T-bird 2 from Mozilla. 

I used to use [Moztray biff]("http://moztraybiff.mozdev.org/releases.html") to minimise TBird to the tray and for the new mail notification. I like to leave it open and have it back in a flash. Especially since I haven't figured out how to have Tbird open to my inbox every time instead of the welcome screen. Anyway . . .

Moztraybiff says it's not compatible with my version of T-bird. I already looked for the 'Nightly Tester Build tools' extension but couldn't find it. I did install an extension called 'nightly tester build tools lite,' but it didn't let me get away with using the moztray extension. 

What do you other Thunderbird addicts suggest I use to minimise TB to the tray/notification area?

Kolin

---

### Post by Brucevdk on 2007-04-20
I use [AllTray]("http://alltray.sourceforge.net/") from [Asher256's repository]("http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en"), it enables you to send any program to the system tray by closing it. All you have to do is start it like:

```

alltray mozilla-thunderbird

```

---

### Post by kolinab on 2007-04-20
Yeah, thanks for that. I got it working OK. Somehow I had forgotten about Alltray. I will miss the new mail notification in the notification area. 

Anyway, vast improvement. Thanks again.

Kolin

---

### Post by Brucevdk on 2007-04-20
> **kolinab said:**
>  I will miss the new mail notification in the notification area.

The mail notification feature of Thunderbird 2.0 (alerts) works fine in combination with AllTray, actually that's how I found out you replied to this thread :) 

You just can't click it to bring up Thunderbird while it's in the system tray. Actually, it looks like you sorta can, you just have to double click.

---

### Post by kolinab on 2007-04-20
Hmm. So you are right again. Thanks. I like the alerts in TB2, but I guess what I meant to say was I miss the little 'new mail icon' that moztray used to provide. When I had new mail, the t-bird icon would switch to a little envelope, that way if I was away from the computer when a new message came in (which I usually am) I can see if there is anything new just by glancing at the notification area, and I don't have to bring up Thunderbird.

As it is, if I miss the T-bird alert, that's all I get!

But I like alltray, It's going to pacify me for now!

Cheers,

Kolin

---

### Post by spotman on 2007-04-25
hola,

I actually found a workaround for this.

If you open thunderbird,

go to preferences,  go to advanced, go to config editor


right click on the config editor, add a new "boolean" key.

type:

extensions.checkCompatibility

click ok, set it to FALSE.

Then, go to this page:

[http://moztraybiff.mozdev.org/releases.html](http://moztraybiff.mozdev.org/releases.html)

download 1.2.2, and install it normally under the thunderbird add-ons menu.

I haven't fully tested it yet, but seems to be working good so far, at least as good as teh minimizing to tray.  I am not sure the new mail icon feature totally works.

GL,
-spot

ps - this post is now accurate ;)  i had a typo.

---

### Post by kolinab on 2007-04-25
Spotman,

Your workaround got me all excited. I tried it but must be doing something wrong. T-bird is still doing the compatibility check. I made the boolean key, named it, set it false, and tried to install moztray biff 1.2.2 - I am informed by t-bird that the extension is incompatible. 

I'll double check your instructions and my spelling and everything, but so far no-go for me.

Kolin

---

### Post by spotman on 2007-04-25
hi again,

its also possible that im not good w/ instructions :)

one thing, is that you do need to turn it on, and it will always have the warning in the add-on panel that its not compatible, but it should definitely let you install it.

here are some pics to help explain

[http://spotman.net/tbtray/tb1.png](http://spotman.net/tbtray/tb1.png) (you can see its minimized to tray)
[http://spotman.net/tbtray/tb2.png](http://spotman.net/tbtray/tb2.png) (extensions panel)
[http://spotman.net/tbtray/tb3.png](http://spotman.net/tbtray/tb3.png) (tray preferences)
[http://spotman.net/tbtray/tb4.png](http://spotman.net/tbtray/tb4.png) (config editor thing)

GL!!!

-spot

ps - fwiw, I installed thunderbird from the offical mozilla website.

---

### Post by kolinab on 2007-04-25
Hey again Spotman,

I checked your screenshots - learned it's:

extensions.checkCompatibility not extensions.compatibilityCheck

Made the new key, everything works perfectly! Super good, seems to be working well now on initial run. 

Thanks a lot for the workaround, I think it's great.

One thing, do you know how to delete a key from the config editor? I want to delete the key I mis named 'extensions.compatibilityCheck'

K

---

### Post by spotman on 2007-04-25
> **kolinab said:**
> Hey again Spotman,

I checked your screenshots - learned it's:

extensions.checkCompatibility not extensions.compatibilityCheck

Made the new key, everything works perfectly! Super good, seems to be working well now on initial run. 

Thanks a lot for the workaround, I think it's great.

One thing, do you know how to delete a key from the config editor? I want to delete the key I mis named 'extensions.compatibilityCheck'

K

"oops" heh

sorry bout that.  fixed my above post.

as for removing the bad key,

in an editor open up
~/.thunderbird/<weird random hash number>/prefs.js

completely remove the bad line, then save, close n restart tb.

cheers :)

---

### Post by kolinab on 2007-04-26
Note to those interested:

This workaround works for installing the extension, but the extension doesn't quite work perfectly on my system (which has got nothing to do with the workaround as far as I can figure). The 'new mail icon' doesn't work for me, but the minimise to tray feature works as expected. Still valuable for what it does - I think it's preferable to using Alltray.

K

---

### Post by kobewan on 2007-04-27
Does this make your tray icon freakishly small as well? I seem to remember that the icon size was normal in TB1.5. I'm using Kubuntu, so I'm just going to continue to use kdocker for this.

---

### Post by kolinab on 2007-04-27
> **kobewan said:**
> Does this make your tray icon freakishly small as well? I seem to remember that the icon size was normal in TB1.5. I'm using Kubuntu, so I'm just going to continue to use kdocker for this.

Yes, it does make the tray icon significantly smaller. However, while investigating this problem I discovered that the T-bird icon in the top left corner of the program window, and the icons on minimised windows in the window list are all this same size. It was better before. My launcher icon is the proper size. Hmmm. Just realised Firefox is the same way.

---

### Post by Kent84 on 2007-04-30
I am trying to use the "New Mail Icon" extension in conjunction with alltray to achieve the same capabilities as the "minimise to tray" extension (no linux support).

I like alltray because I can close the window so that thunderbird is not in my windows list but have it still in my tray. Unfortunately there the icon in the tray does not change to indicate I have new mail... so I want to use Moztray biff solely for that but that doesn't seem to work...

I am using Thunderbird 2.0.0 on Fiesty Ubuntu. I have disabled the backward compatibility check (as mentioned in this post) and have the "show icon in tray when new message arrives" option ticked. Can anyone help?

---

### Post by kolinab on 2007-05-06
I neved did get this working to my satisfaction. I did receive, however, an email today from the developer, who tells me that there will be a new version soon.

That sounds nice!

---

### Post by termite on 2007-05-10
This might work: [http://translate.google.com/translate?hl=en&sl=de&u=http://www.fritteli.ch/2007/04/10/moztraybiff-fuer-thunderbird-2/&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3D%2522thunderbird%2B2%2522%2Bmoztraybiff%26num%3D100%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DKpz%26sa%3DG](http://translate.google.com/translate?hl=en&sl=de&u=http://www.fritteli.ch/2007/04/10/moztraybiff-fuer-thunderbird-2/&sa=X&oi=translate&resnum=1&ct=result&prev=/search%3Fq%3D%2522thunderbird%2B2%2522%2Bmoztraybiff%26num%3D100%26hl%3Den%26client%3Dfirefox-a%26rls%3Dorg.mozilla:en-US:official%26hs%3DKpz%26sa%3DG)

works for me!

---

### Post by kolinab on 2007-05-11
A joy to read! hehe, great. I will try this soon. Thanks for the link.

---

### Post by ffxr on 2007-05-13
show has anyone got the new mail icon working yet? 

the Moztray biif link above is for 2.00 thunderbird.. i dont understand.. i NEED my new mail icon.

help.

---

### Post by ffxr on 2007-05-13
right ive upgraded to Thunderbird 2: [https://help.ubuntu.com/community/ThunderbirdNewVersion](https://help.ubuntu.com/community/ThunderbirdNewVersion)

installed the mozbifftray..from link just above... but still no icon in my system tray..

hmmmmmmmmm


[on ubuntustudio 7.04 btw]

---

### Post by kolinab on 2007-05-13
Yeah, it doesn't work for me either. Just tried it for the first time now. I had better luck using the original moztray biff and disabling extension compatability checking . . . I guess I just wait for the extension to get updated. I have learned to live with it - in the end it is no longer a big deal for me. I guess when it is working again it will be a treat.

Once again I have learned to stay off the cutting edge. I could have (maybe I will go back?) stayed with TB 1.5 and had things the way I wanted them.

---

### Post by roberthr on 2007-05-16
I found updated version of this extension that should work with TB 2 on page [http://www.fritteli.ch/2007/04/10/moztraybiff-fuer-thunderbird-2/](http://www.fritteli.ch/2007/04/10/moztraybiff-fuer-thunderbird-2/)

EDIT: Does not work :-(

---

### Post by nischg on 2007-05-16
> **roberthr said:**
> I found updated version of this extension that should work with TB 2 on page [http://www.fritteli.ch/2007/04/10/moztraybiff-fuer-thunderbird-2/](http://www.fritteli.ch/2007/04/10/moztraybiff-fuer-thunderbird-2/)

EDIT: Does not work :-(

The guy in that post says he compiled the file. Maybe he did that for his locale and thats the reason it does not work for us. I'll tray later to compile the file myself.

---

### Post by roberthr on 2007-05-17
Please please :-)

I really miss that function.

---

### Post by nischg on 2007-05-20
I ve managed to compile the damn thing with a lot of symlink problems, but it doesnt work. it installs but no icon is showed. ill keep trying

---

### Post by atze76 on 2007-05-22
There is a new release of moztraybiff for TB2.0

[http://moztraybiff.mozdev.org/releases.html](http://moztraybiff.mozdev.org/releases.html)

But for some reason, even with the new version the mail notification icon doesn't appear in my system tray :-(

---

### Post by jewishj on 2007-05-22
If you look at the options for the extension it appears that you can either have the icon only show up when there is a new message or be there all the time but not change when a new message shows up - if that makes any sense.

I was able to get the desired effect by installing the extension and unchecking the "always in tray" option, then using alltray to launch thunderbird.  So, alltray keeps an icon in the tray, and the extension will show another icon in the tray when a new message shows up.

By the way, does anyone know if there is a handle or something so that all tray will let me close (via the close button or alt-F4) to minimize to tray rather than just letting me toggle it by clicking on the tray icon?  Right now, closing the alltrayed TB this way will close alltray also.  This used to work perfectly when I was running dapper + TB1.5 but now that I have feisty + TB2 - it doesn't.

UPDATE:  Actually, adding & at the end of the launcher made it so that the close button now works correctly - however alt-F4 still closes alltray... weird

Thanks

---

### Post by atze76 on 2007-05-22
My problem is not that the icon does not disappear. The problem is that it does not show up at all :-(

---

### Post by roberthr on 2007-05-22
Finaly!!!! Works properly by me. Like it used to with 1.5.

---

### Post by Circlingthesun on 2007-05-23
There is a new version out for TB 2:

[http://moztraybiff.mozdev.org/releases.html](http://moztraybiff.mozdev.org/releases.html)

:D

---

### Post by kolinab on 2007-05-24
And there was much rejoicing.

Also, why is it called a 'biff?' inquiring minds want to know.

K

---

### Post by foxy123 on 2007-05-25
> **kolinab said:**
> And there was much rejoicing.

Also, why is it called a 'biff?' inquiring minds want to know.

K

I guess because of that:
> The interface itself doesn't have any members: it's simply a way for us to bootstrap (using NS_GENERIC_FACTORY_CONSTRUCTOR_INIT) whenever Mozilla Mail opens and to sign up as a folder observer and wait for **[COLOR="Blue"]BiffState [/COLOR]**changes. The tray icon GTK code was taken from libegg.

---

### Post by legolas_w on 2007-05-25
Hi
Is there any way to remove thunderbird from window list panel (in bottom of screen) and just let it be present in system try?

I do not want my window list panel to be very crowded and my thunderbird is allways open.

in windows it was possible using an extension.



Thanks

---

### Post by kobewan on 2007-05-25
> **legolas_w said:**
> Hi
Is there any way to remove thunderbird from window list panel (in bottom of screen) and just let it be present in system try?

I do not want my window list panel to be very crowded and my thunderbird is allways open.

in windows it was possible using an extension.



Thanks

A work-around to this problem is to do what I do; use a program called "kdocker" to get the system tray icon. kdocker also has an option to skip the taskbar. You would run it with "kdocker -t mozilla-thunderbird". You can try some other options as well, I've found that the best suited for me is "kdocker -d -m -q -t mozilla-thunderbird"

---

### Post by luger on 2007-09-20
When I run kdocker to dock Thunderbird, I get an error message:

> X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Sorry, your locale is not supported. If you are interested in providing translations for your locale, contact [email]gramakri@uiuc.edu[/email]

Despite saying that, it still adds the Thunderbird icon and such to the dock but I'm not sure if that error message is telling me anything I should be aware of.  Anybody know?

---

### Post by luger on 2007-09-20
Okay, I closed Thunderbird then opened again and now it won't go into the dock. If I minimize, it just goes back to the Window List. Anybody have any problems like this with kdocker before and know the solution?

---

