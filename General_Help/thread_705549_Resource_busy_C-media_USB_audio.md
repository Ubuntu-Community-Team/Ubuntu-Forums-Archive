---
title: "Resource busy C-media USB audio"
date: 2008-02-23
forum: General Help
---

### Post by ragor on 2008-02-23
I'm using a USB sound device that came with my headset [**[COLOR="Blue"]Plantronics audio 650[/COLOR]**]("http://www.bestbuy.com/site/olspage.jsp?skuId=8497842&productCategoryId=abcat0515040&type=product&tab=2&id=1186004297442#productdetail") and I have noticed that it only seems to allow one application to provide sound.
If I was running firefox, I could listen to sounds from youtube or anything else that was embedded. But if I tried starting up rhythmbox to play some music in the background, no sound would play. The only sound that would work was through firefox.

But if i was to close firefox and restart rhythmbox then I would hear sound but only from rhythmbox and nothing else. All other applications exhibit the same behavior, skype, totem, and the sound tester in the sound preferences which gives me the error:
```
audiotestsrc wave=sine freq=512 ! audioconvert !
audioresample ! gconfaudiosink: Resource busy or not available.
```

---

### Post by ragor on 2008-02-27
My onboard sound works fine however it produces a static sound whenever I move my mouse due to interference.

---

### Post by tpost001 on 2008-04-19
I see that no one has responded to you yet.  I don't have the answers.  I wish I did.  I have the same problem.  I can get the nice Ubuntu log in drum beat and I hear Skype startup with its woosh sound, but then from then on I hear nothing.  When I go to System>Preference>Sound and choose anything from the drop down menus and click on Test, I get the same error message as you do.  I just wish there was a way to figure out what else is using it and try and disable it.

---

### Post by thebigbluecan on 2008-05-15
Im having the same problem... but with my sound card. It also is the case on another computer (Dell) also. I'm wondering if I should report it as a bug. I couldn't find it on bugs.launchpad.net   ....Its really annoying to have to quit a program to get sound from another program. I't didnt happen for me on 7.10 ... Only when I went to 8.04

---

