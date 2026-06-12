---
title: "firefox broken"
date: 2008-05-13
forum: General Help
---

### Post by jamesjeffries1 on 2008-05-13
when i open firefox in hardy none of my mylinks are displayed. also my history and favourites arent there. the back and forward button aren't enabled. The address bar is always empty.

It worked originally but i cant think of any thing which i might have changed that could have caused this.

Any ideas?
Thanks
James

---

### Post by pytheas22 on 2008-05-13
Try opening Firefox in a terminal (just type "firefox" at the command line) and see if the output that gets reported gives any information about what's wrong.

Also you should try making a second user account on your system and running Firefox there.  This would tell you whether the problem lies with Firefox itself or with your user configuration.

You could also try using Synaptic to do a complete removal of Firefox and then reinstall.  Be careful not to inadvertently uninstall any important programs that might depend on Firefox (there should be none, but just make sure to read the list of applications to be removed before pressing ok).

---

### Post by jamesjeffries1 on 2008-05-13
i have tried reinstalling through the package manager and have tried running it through the command with out any output. No luck with the new user either still the same problem

---

### Post by egorgry on 2008-05-13
what do you mean by none of my mylinks? Is it a typo or am I ignorant to this? I ask because I use foxmarks in ffB5 and if that extension is installed on version 2.x of ff it can wipe out the bookmarks when it does it's sync.

edit for clarification. 

if I have foxmarks installed on FF3b5 on my lappy and FF2.x on Desktop when foxmarks tried to sync between the tow version is then wipes the bookmarks and it's a known issue.

Is mylinks an extension?

---

### Post by pytheas22 on 2008-05-13
Are you using the Firefox 3 beta or Firefox 2?

---

### Post by jamesjeffries1 on 2008-05-14
sorry, force of habit from a browser i wrote ages ago. its the bookmarks toolbar. just tried making another user again (realised i did it lsat time and then just logged in with my old account!) and it works fine in that account.

Guessing that means its something to do with my configuration

The version of firefox i'm using is firefox 3 beta 5

Thanks

---

### Post by SammyBoy247 on 2008-05-14
I've got exactly the same issue.

Firefox 3.0b5 under x64 ubuntu 8.04

The problem started out of the blue one day.  It's as if firefox has no access to the history.  It gives you no predictions of addresses as they are typed, it has no back button and, of course, no content in the history panel.

I've reinstalled
          firefox, firefox-3.0 and firefox-3.0-gnome-support

problem persisted

I then completely removed
          firefox, firefox-3.0, firefox-3.0-gnome-support, ia32-lib-firefox, ubufox, mozilla-firefox-locale-en-gb

and installed 
          firefox-3.0

Still not working

I think i'm going to step back a version unless someone has any better ideas.
Running from bash gives no error messages.

By the way opera 9.5b2 is also buggy on my system and occasionally just ends and disappears.

Looks like i'm going to have to do something useful instead of hours of surfing.

Any help much appreciated.

---

### Post by pytheas22 on 2008-05-14
You both could try running:
```

mv ~/.mozilla ~/.mozilla.backup
```

In principle this should erase your local user configurations for Firefox and hopefully solve the problem.  If it does, you can try restoring moving your bookmarks and other important settings back in, but at least try this to see if it solves the problem.

---

### Post by SammyBoy247 on 2008-05-14
> **pytheas22 said:**
> You both could try running:
```

mv ~/.mozilla ~/.mozilla.backup
```

In principle this should erase your local user configurations for Firefox and hopefully solve the problem.  If it does, you can try restoring moving your bookmarks and other important settings back in, but at least try this to see if it solves the problem.

up and running again.

So simple - thank-you.

---

### Post by rMatey on 2008-05-27
I had the same problem.  I uninstalled and reinstalled all of the Firefox and plugin packages.  Nothing seemed to work.
  I found a backup file of the Firefox settings in my Home folder.  What hte "H".  I deleted it and shortly Firefox would run again.
  Maybe I just got lucky.

---

### Post by stevelasvegas on 2008-08-10
That fixed it for me! Thanks pytheas22.

---

### Post by starlily on 2008-10-23
I had this exact problem also. 

I looked in ~/.mozilla/firefox/<randomness>.default and noticed places.sqlite-journal had no permission at all (----------). 

So I did: chmod u+rw ~/.mozilla/firefox/<randomness>.default/places.sqlite-journal

And all was well. 

Peace, 
Lily

---

### Post by Runamok on 2009-03-26
Had this same issue, it was in conjunction with a few other problems like not being able to D/L with firefox (not enough room in /tmp...) 

This was caused by my hardrive being almost full.  I had to clear out some old files, and then
sudo gedit /etc/mtab
And delete some setting that was intiated by Ubuntu as a safety measure.

---

### Post by braddcadd on 2009-04-14
> **starlily said:**
> I had this exact problem also. 

I looked in ~/.mozilla/firefox/<randomness>.default and noticed places.sqlite-journal had no permission at all (----------). 

So I did: chmod u+rw ~/.mozilla/firefox/<randomness>.default/places.sqlite-journal

And all was well. 

Peace, 
Lily

That got it for me, thanks Lily

---

### Post by ndmaque on 2009-05-09
> **pytheas22 said:**
> You both could try running:
```

mv ~/.mozilla ~/.mozilla.backup
```

In principle this should erase your local user configurations for Firefox and hopefully solve the problem.  If it does, you can try restoring moving your bookmarks and other important settings back in, but at least try this to see if it solves the problem.

Thanks for this solution.

i had nothing in the address bar and no back buttons or history. Links worked ok and pages loaded ok but nothing showed in the location bar. I created a new user and FF was working fully so it had to be a conf.

---

### Post by zigga15 on 2009-08-01
Mine broke as well...

The last 2 years I have been using ubuntu I have occasionally run into the problem.

Seems to always happen after an update. This is really really annoying, so I switch to opera - although it is not my perfered browser.

My guess is the devs have been a bit ambitious and are shipping unstable software that hasn't been thoroughly tested --- Although this is just a n00bs assumption and I don't intend to start a flame war.

If anyone else knows the reason why this is happening, please enlighten me.

~ Dan

---

### Post by zuctronic on 2009-10-01
> **zigga15 said:**
> Mine broke as well...

The last 2 years I have been using ubuntu I have occasionally run into the problem.

Seems to always happen after an update. This is really really annoying, so I switch to opera - although it is not my perfered browser.

My guess is the devs have been a bit ambitious and are shipping unstable software that hasn't been thoroughly tested --- Although this is just a n00bs assumption and I don't intend to start a flame war.

If anyone else knows the reason why this is happening, please enlighten me.

~ Dan
mv or rm you ~/.mozilla directory and your back arrow, history, location field, etc. will work again

---

