---
title: "Firefox slow -- plugin-container network hog"
date: 2014-10-21
forum: General Help
---

### Post by b00n on 2014-10-21
I noticed recently Firefox is sometimes very slow, I do not know what changed that it stopped being fast.

It appears this process

```
/usr/lib/firefox/plugin-container -greomni /usr/lib/firefox/omni.ja -appomni /usr/lib/firefox/browser/omni.ja -appdir /usr/lib/firefox/browser 2367 true tab
```

Is hogging all the network for quite a while; if I kill the process, network use falls like a rock and Firefox is fast again... until it starts another one of these (which is usually soon).

Just opening a new tab causes Firefox to launch one and hog the network.  Most of the traffic is download, but some upload.

I disabled all add-ons and restarted Firefox, same problem.  Installed/enabled NoScript, same problem.

Recent Ubuntu, about 2 months old; I disabled as much of the Unity/Lens stuff as I could find.  I think the problem is about a week old, but I wasn't really paying attention so maybe much older.

A couple questions:

(a) What purpose is this plugin? I see no reason opening a new tab should cause any network traffic.  At the same time, I can kill the process and the only obvious change is things get faster, again I wonder why it is there.

(b) What can I do so it is not a hog?  Opening a new tab seems to transfer about 10 Megabytes.  On a flat-rate but slow network this is merely annoying.  On a pay-as-you go network (e.g., phone tether) this is also expensive.

I am guessing somebody on the receiving end of this traffic is unhappy, too :^(

---

### Post by vasa1 on 2014-10-23
I think you should see "/usr/lib/firefox/plugin-container -greomni" only when you're running Flash and not otherwise.

Have you tried setting Flash to "ask to activate" in the plugins tab of about:addons?

---

### Post by b00n on 2014-10-23
> **vasa1 said:**
> I think you should see "/usr/lib/firefox/plugin-container -greomni" only when you're running Flash and not otherwise.

I have several "commercial" pages open and it is possible one/some were running Flash.  I'd find that a little bit odd in that I was experiencing the problem for a while and it seems like I close pages often enough a "rogue" page would have gone away.

But, I could be wrong!

> Have you tried setting Flash to "ask to activate" in the plugins tab of about:addons?

I had not.  That is also something I have not changed recently, so I do not know why it would suddenly start mis-behaving.

But!

I set it to "ask" (as suggested) went to a site with Flash, okay use, start playing Flash... Flash crashes, reload page, everything works fine.  Pause the flash, now I open a new tab (which was all it took before) and ... no network traffic.  The plugin container is running, but even after opening a bunch of tabs it does not gain any CPU time.  I further tried re-enabling "run without asking" and still on new tab, no network traffic.

I suppose it could be


[LIST]
[*]some bad state that got "fixed" in switching the "ask to activate" setting 
[*]some bad state that was "fixed" by crashing Flash and having it restart, which may have reset some Firefox state 
[*]something else I accidentally changed in the last 24 hours (e.g., closed an offending web page) 
[/LIST]

So the good news is the symptom seems gone.

I am still confused about why it was there in the first place -- when I open a new tab, it shows a bunch of (what look like) static images, if I look at the page source there's nothing suggesting Flash.

"ask to activate" seems like a good thing to have on, anyway, so I re-enabled that.  Thanks also for telling me about it.

I guess this is "case closed" at least until the symptom re-appears.  Maybe never :)  Thanks!

---

### Post by vasa1 on 2014-10-23
> **b00n said:**
> ...
"ask to activate" seems like a good thing to have on, anyway, so I re-enabled that.  Thanks also for telling me about it.
...
There are also dedicated extensions to help you control Flash. I don't use them but other forum members do. Maybe someone will suggest something :)

---

### Post by b00n on 2014-11-26
It's baaaaack!

:^(

I disabled Flash entirely (about:addons > Shockwave Flash > "Never Activate"), exited Firefox (actually, rebooted) and if I just open a new tab, Firefox will start a new plugin-container and hog all my network bandwidth as described above.

This is Firefox 33.0 (as reported by Help > About).

I note that opening a new tab shows a tile of thumbnails for previously-open windows/tabs.  I would expect those are just static images, but maybe the attempt to show past pages is somehow starting the plugin container?  I did something like


[LIST]
[*]Go to URL [FONT=courier new]about:config[/FONT] 
[*]Read warning "this could void your warranty" text, click on [FONT=courier new]I'll be careful, I promise[/FONT] 
[*]Search for [FONT=courier new]browser.newtab.url[/FONT] 
[*]Double-click on it and change "value" to [FONT=courier new]about:blank[/FONT] 
[/LIST]
 
Now "new tab" does not start plugin-container, though I have not been using this long enough to have an opinion if all the oinky-oinky problems are gone, but I thought I'd mention sooner rather than later in case somebody else is having the same problem.

Too bad, I like the shortcuts, and I don't know why it would need to download 10 MiB off the network -- heck, I don't know why it would need to download anything.

---

### Post by b00n on 2014-11-26
> **b00n said:**
> 
Too bad, I like the shortcuts, and I don't know why it would need to download 10 MiB off the network -- heck, I don't know why it would need to download anything.

Or: why it would only happen sometimes.

---

