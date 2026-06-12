---
title: "Firefox Takes Over Full Screen - why?"
date: 2008-05-04
forum: General Help
---

### Post by Jackie_Treehorn on 2008-05-04
Strange problem that just started happening.  When I launch Firefox, it will take over the whole screen...including the top and bottom panel of my Ubuntu desktop.  The panels are set to always show by the way.  I've changed nothing there from the original settings.

There are not even any minimize, maximize, close buttons on the Firefox window.  And no title bar for Firefox either.

I can get everything back to normal by hitting F11 for full screen and then hitting F11 again.  But that is not the solution.

Thanks,

Jackie
8.04

---

### Post by hashimoto on 2008-05-05
Same happens here.

Hashimoto

---

### Post by Jackie_Treehorn on 2008-05-10
Don't know why, but it seems to have solved itself.

---

### Post by xjgnsdof on 2008-05-10
That happened to me on a hot day with no AC. I think it's the video card screaming for some fresh (cold) air.

---

### Post by EricDB on 2008-09-23
This has always been the case for me--I thought it was by design.  I wish I could keep my panel visible.  Any idea what the fix could be?

---

### Post by sam1948 on 2009-01-28
joining the request

---

### Post by sam1948 on 2009-01-28
ok i solved it but very dirty solution
run in terminal
```
sudo apt-get remove firefox*
```

run search as super user
```
sudo gnome-search-tool
```
search the file-system for firefox
select all results and delete them
search the same for mozilla and delete all

and finally reinstall a clean new copy of firefox
```
sudo aptitude install firefox
```

it worked perfect for me but the massive deleting can be a bit risky 

Bests

---

### Post by Haiyadragon on 2009-01-28
I think this has something to do with the compiz workarounds. In the CompizConfig Settings Manager (ccsm), try fiddling with the options under Workarounds.

---

### Post by kyphi on 2009-01-28
Press F11 to get full screen - press F11 to return to normal screen.

---

### Post by Tomatz on 2009-01-28
> **sam1948 said:**
> ok i solved it but very dirty solution
run in terminal
```
sudo apt-get remove firefox*
```

run search as super user
```
sudo gnome-search-tool
```
search the file-system for firefox
select all results and delete them
search the same for mozilla and delete all

and finally reinstall a clean new copy of firefox
```
sudo aptitude install firefox
```

it worked perfect for me but the massive deleting can be a bit risky 

Bests

Surely:

```
sudo apt-get remove --purge firefox && sudo apt-get install firefox
```


Would be better???

---

### Post by Bupsss on 2009-01-28
as far as i remember is a problem with firefox settings... delete the folder in home, .mozilla it will create it again and firefox should work.

Of course if you have all your settings, just rename it, and then import the data.

---

### Post by sam1948 on 2009-01-28
Tomatz. of course, it's much better .

```
sudo apt-get remove --purge firefox && sudo apt-get install firefox
```

learning new thing every day:oops:

---

### Post by Tomatz on 2009-01-28
> **sam1948 said:**
> tomatz. Of course, it's much better .

```
sudo apt-get remove --purge firefox && sudo apt-get install firefox
```

learning new thing every day:oops:

Thats fine :D

---

### Post by Therion on 2009-01-28
F11 key, (two times), is the quick-fix for this problem but gets annoying pretty quickly.

For some, the Compiz workaround solves the problem:

Open CCSM.
Go to the Utilities section and open the "Workarounds" plugin.
DE-Select (turn off) the check box for **Legacy Fullscreen Support**.

You may need to log out and back in to make the CCSM fix "stick", I can't remember.

---

### Post by BetterAndBetter on 2009-02-15
I started having problems with more applications than just Firefox taking over the complete screen, e.g., kmail, etc.  The compizconfig-settings-manager fix seems to be working for me.

8.10 has been the worst Ubuntu release for me so far.  I hope 9.04 is a LOT BETTER.

:lolflag:

---

### Post by perpetualcacophany on 2009-02-15
I had this same problem a couple days ago.

I went into workarounds in ccsm and unchecked Legacy Fullscreen Support. It fixed my problem.

---

### Post by sam1948 on 2009-02-16
> **BetterAndBetter said:**
> I started having problems with more applications than just Firefox taking over the complete screen, e.g., kmail, etc.  The compizconfig-settings-manager fix seems to be working for me.

8.10 has been the worst Ubuntu release for me so far.  I hope 9.04 is a LOT BETTER.

:lolflag:

i don't agree. this is the first time _every thing_ worked for me 
until now with all distributions i have had to choose between one that my printer works with and a one the video card worked with
i believe u just have to find the best distro' fits with u'r hardwre
(ibm t30,radeon 7500 mobility, epson stylus cx4300, tp-link usb wifi tl-wn321g)

regards

---

### Post by prkos on 2009-02-17
Thank you! 

I fixed Firefox earlier using that f11 twice method, I'm not sure exactly how it goes. 

But now after the update lots of KDE applications behaved like weird full screen, and turning Legacy Fullscreen Support off fixed it.

---

### Post by digitalpulse on 2009-03-01
> sudo apt-get remove --purge firefox && sudo apt-get install firefox


This worked a treat for me after a page specifically for IE killed firefox and put the browser into a loop reopening page. The fullscreen thing started up on reboot and then I came across the above command. Thanks for the help....BTW what is being purged in the command?  Thanks.

---

### Post by steveneddy on 2009-03-02
> **Therion said:**
> F11 key, (two times), is the quick-fix for this problem but gets annoying pretty quickly.

For some, the Compiz workaround solves the problem:

Open CCSM.
Go to the Utilities section and open the "Workarounds" plugin.
DE-Select (turn off) the check box for **Legacy Fullscreen Support**.

You may need to log out and back in to make the CCSM fix "stick", I can't remember.
[B]
This actually is the correct fix for that issue.[/B]

---

### Post by mdgrech on 2009-03-02
I was having this same problem with firefox and Inkscape unable to resize, Bumping up my monitor resolution solved it.  Hope that helps someone :)

---

### Post by HuaiDan on 2009-03-02
You know guys, this was annoying the F*&% out of me for weeks.

Then I discovered something. If you mouse up to where the title bar should be, then your window controls re-appear, if you hang there for a second. Now I kind of like the feature. Alt-tab still flips your apps, desktop icon still shows desktop, so what's not to like about it once you learn how to manage it?

Of course F11 works too. Almost cost me a divorce trying to find that.


Thanks for the compiz workaround workaround, I'll try it asap.

---

