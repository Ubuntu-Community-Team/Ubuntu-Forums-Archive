---
title: "IEs 4 Linux problem"
date: 2008-01-18
forum: General Help
---

### Post by teejay17 on 2008-01-18
I have a problem. Internet Explorer 6 is now installed, but the toolbars at the top, as well as the address bar, text boxes on web pages, etc. are all gray and the fonts are not appearing. Basically, all text within the program is not appearing, and the white boxes are also not appearing. (Web pages, however, are showing up fine.)
Does anyone know what I'm talking about, or has anyone experienced this? More importantly: how can I fix this?

---

### Post by lian1238 on 2008-01-18
Can we get a screenshot please?
Also, could you try running it from the terminal?
```
ie6
```
Then, could you paste the output from the terminal here?

---

### Post by teejay17 on 2008-01-18
> **lian1238 said:**
> Can we get a screenshot please?
Also, could you try running it from the terminal?
```
ie6
```Then, could you paste the output from the terminal here?
I can't put a screenshot; I've already tried, but the forum won't let me.
When I open ie6 from the terminal, I get the same results: no fonts, gray toolbars. 
[IMG]http://ubuntuforums.org/home/teejay17/Desktop/Screenshot-Internet%20Explorer:%20Get%20It%20Now%20-%20Microsoft%20Internet%20Explorer%206.0.png[/IMG]

---

### Post by Sam on 2008-01-18
> **teejay17 said:**
> I can't put a screenshot; I've already tried, but the forum won't let me.
When I open ie6 from the terminal, I get the same results: no fonts, gray toolbars. 
[IMG]http://ubuntuforums.org/home/teejay17/Desktop/Screenshot-Internet%20Explorer:%20Get%20It%20Now%20-%20Microsoft%20Internet%20Explorer%206.0.png[/IMG]

Use [ImageShack](http://imageshack.us/) to upload an image.

lian1238 suggested you to post the console output when you run 'ie6'. Example:
```
$ ie6
fixme:spoolsv:serv_main (0 (nil))
err:shell:ReadCabinetState Initializing shell cabinet settings
fixme:shell:DllGetClassObject failed for CLSID=
        {53bd6b4e-3780-4693-afc3-7161c2f3ee9c} (MruLongList)
etc...
```

---

### Post by UbUsOsOlik on 2008-01-18
I dont understand wy you use IE, just use firefox, faster better and free.

---

### Post by Sam on 2008-01-18
> **UbUsOsOlik said:**
> I dont understand wy you use IE, just use firefox, faster better and free.

Maybe web development, or access to a IE only website ???

---

### Post by UbUsOsOlik on 2008-01-18
I dont think that there is any site that dosent suport firefox, the new versions from firefox suports every thing posible. Mabe you are right , web development

---

### Post by pawsey on 2008-01-18
I'm having this problem too: here's my attached screen shot of ie6 - the "missing" fonts appear to be the same colour as the grey background.

Nothing appears in terminal after I type ie6 so have not posted that image.

I use ie6 because I use msmoney 4, which now has an identical problem - ie fonts hidden by same colour background.


Note I cannot access fonts in the Wine Config tool - Desktop Integration tab


NB I am using the most recent version of ie6. Apologies for poor screenshot - my first!

---

### Post by Borbus on 2008-01-18
> **UbUsOsOlik said:**
> I dont understand wy you use IE, just use firefox, faster better and free.

I think it is safe to assume that it is for web development ie. testing websites in IE. I just use a Windows XP installation in VirtualBox, though. I have IE6 and IE7 running standalone (using these instructions: [http://tredosoft.com/IE7_standalone](http://tredosoft.com/IE7_standalone) ). I have the state saved in VirtualBox so it takes literally 2 seconds to start it up and the mouse pointer integrates straight into it (you have to have the guest extensions which you don't get with the OSE version of virtualbox, so get the personal use edition, free as in beer, from the site).

---

### Post by sistoviejo on 2008-01-18
> **UbUsOsOlik said:**
> I dont think that there is any site that dosent suport firefox, the new versions from firefox suports every thing posible. Mabe you are right , web development

I have seen some. But no more than 2 or 3.
This site here doesn't support firefox:
[http://www.brounet.com.uy/](http://www.brounet.com.uy/)
The menu on the left isn't clickable.  :(
It works fine on IE6 though.

---

### Post by lian1238 on 2008-01-18
> **UbUsOsOlik said:**
> I dont understand wy you use IE, just use firefox, faster better and free.
I use IE cuz my university's website only works with IE. With FF, the main section of the page is replaced with a link "Click Here to Use". I click, then "Page Not Found (404)" appears with some long message.

---

### Post by pawsey on 2008-01-18
Issue now resolved in a roundabout way - the final permutation which worked for me was:

Uninstalling ies4 and wine (version 0.9.53), 

Reboot.
 
Then install previous wine version 0.9.51.
 
Reinstalling ies4. 

Reinstall MSMoney 4.

Finally, update wine to current version: 0.9.53.

Everything working AOK now.

---

### Post by teejay17 on 2008-01-19
> **pawsey said:**
> I'm having this problem too: here's my attached screen shot of ie6 - the "missing" fonts appear to be the same colour as the grey background.

Nothing appears in terminal after I type ie6 so have not posted that image.

I use ie6 because I use msmoney 4, which now has an identical problem - ie fonts hidden by same colour background.


Note I cannot access fonts in the Wine Config tool - Desktop Integration tab


NB I am using the most recent version of ie6. Apologies for poor screenshot - my first!
Sorry everyone, I was at work and couldn't get back to this thread until now.
And yes, that's exactly what my screen looks like too! 
And it's not for web development, or anything like that, but to actually pay bills on my bank's website that will not anything but Explorer pay bills. (Everything shows up fine in Firefox, but when I actually click "pay bills" nothing happens.)

---

### Post by teejay17 on 2008-01-19
> **pawsey said:**
> Issue now resolved in a roundabout way - the final permutation which worked for me was:

Uninstalling ies4 and wine (version 0.9.53), 

Reboot.
 
Then install previous wine version 0.9.51.
 
Reinstalling ies4. 

Reinstall MSMoney 4.

Finally, update wine to current version: 0.9.53.

Everything working AOK now.
Man, that's way too many steps. And I would really like to have IE 6 working. There must be another solution...

---

### Post by lian1238 on 2008-01-19
Right, that seems like alot. Getting the older version might be a little scary, since apt-get install wine will install the latest version. I am using wine version 0.9.53 with no problem. 

Maybe you could try uninstalling both ies4linux and wine, reboot, then reinstalling them both. That wouldn't take a lot of steps. If that doesn't fix your problem, at least we now know a way that'll work for sure.

---

### Post by teejay17 on 2008-01-19
> **lian1238 said:**
> Right, that seems like alot. Getting the older version might be a little scary, since apt-get install wine will install the latest version. I am using wine version 0.9.53 with no problem. 

Maybe you could try uninstalling both ies4linux and wine, reboot, then reinstalling them both. That wouldn't take a lot of steps. If that doesn't fix your problem, at least we now know a way that'll work for sure.
Yeah, I guess...I'm going to uninstall them, but I think I'll just leave them uninstalled:frown:

---

### Post by teejay17 on 2008-01-20
Before I uninstall them, however, I'm going to wait just a little longer. There's got to be a fix, or a patch, or something to get around this little IE6 problem. 
I really don't want to have to use IE6, but I really hate logging into Windows only to do banking. That's the reason why I'd like this to work.

---

### Post by sistoviejo on 2008-01-20
In the meantime you could try complaining to your bank.

Also you can report the incompatibility to Mozilla by opening the "Help" menu and then clicking on "Notify about incompatible web site". The option might be a little different because my Firefox isn't in English.

---

### Post by teejay17 on 2008-01-20
> **sistoviejo said:**
> In the meantime you could try complaining to your bank.

Also you can report the incompatibility to Mozilla by opening the "Help" menu and then clicking on "Notify about incompatible web site". The option might be a little different because my Firefox isn't in English.
Yeah,  that's a good idea too. I never thought about complaining to Firefox.

---

### Post by teejay17 on 2008-01-22
Anyway, it's too bad, but I uninstalled IEs 4 Linux and Wine; my experience with both products thus far has been less than stellar.

---

