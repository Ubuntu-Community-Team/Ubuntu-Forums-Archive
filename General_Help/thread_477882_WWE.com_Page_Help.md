---
title: "WWE.com Page Help?"
date: 2007-06-18
forum: General Help
---

### Post by TheVault on 2007-06-18
Hello guys, I'm having somewhat of a little problem.
When I am on Windows Xp, WWE.com looks just perfect. On my Windows side, I have Java & Flash enabled.

When I am on ubuntu, the page looks a little messed up, just a little annoyance. I also to have Java & Flash installed and enabled.
If your unsure cause you never been to the website, look at my screenshots below:

Ubuntu:
[http://i2.photobucket.com/albums/y28/kylewitt/wwe-ubuntu.png](http://i2.photobucket.com/albums/y28/kylewitt/wwe-ubuntu.png)

Windows XP:
[http://i2.photobucket.com/albums/y28/kylewitt/www-windowsxp.png](http://i2.photobucket.com/albums/y28/kylewitt/www-windowsxp.png)

Whats going on? I have some other websites this happens when I go to them but this website I visite frequently. I'm not here to advertise this website in anyway, I'm just seeing if anyone get similar things to this and if so, how can I fix this if this is fixable. Thanks.

---

### Post by marc321 on 2007-06-18
Well, I'm afraid you'll have to wait until Firefox 3.0 comes out.  I tried it on my computer (Slackware-current with Firefox-2.0.0.4) and got the same results.  I would guess that it is a CSS issue.  Firefox 2 doesn't pass the Acid2 CSS test: [http://www.webstandards.org/files/acid2/test.html]("http://www.webstandards.org/files/acid2/test.html")

However, Konqueror, the KDE browser and file manager, which does pass the test, renders wwe.com just fine.

If you really want to, you might look into downloading the latest alpha build of Firefox 3.0, but it will probably be very buggy.

P.S.  Nice job making your Ubuntu desktop look like Vista.  You had me fooled.

---

### Post by marc321 on 2007-06-18
You could also try installing Opera 9.  It passes the Acid2 test.  I don't have Opera, so I don't know if it renders wwe.com correctly, but it may be worth a try.

---

### Post by Anonii on 2007-06-18
> **marc321 said:**
> Well, I'm afraid you'll have to wait until Firefox 3.0 comes out.  I tried it on my computer (Slackware-current with Firefox-2.0.0.4) and got the same results.  I would guess that it is a CSS issue.  Firefox 2 doesn't pass the Acid2 CSS test: [http://www.webstandards.org/files/acid2/test.html]("http://www.webstandards.org/files/acid2/test.html")

However, Konqueror, the KDE browser and file manager, which does pass the test, renders wwe.com just fine.

If you really want to, you might look into downloading the latest alpha build of Firefox 3.0, but it will probably be very buggy.

P.S.  Nice job making your Ubuntu desktop look like Vista.  You had me fooled.
Windows Firefox passes the Acid2 test, but Linux Firefox doesn't?
Interesting.

---

### Post by TheVault on 2007-06-18
> **marc321 said:**
> Well, I'm afraid you'll have to wait until Firefox 3.0 comes out.  I tried it on my computer (Slackware-current with Firefox-2.0.0.4) and got the same results.  I would guess that it is a CSS issue.  Firefox 2 doesn't pass the Acid2 CSS test: [http://www.webstandards.org/files/acid2/test.html]("http://www.webstandards.org/files/acid2/test.html")

However, Konqueror, the KDE browser and file manager, which does pass the test, renders wwe.com just fine.

If you really want to, you might look into downloading the latest alpha build of Firefox 3.0, but it will probably be very buggy.

P.S.  Nice job making your Ubuntu desktop look like Vista.  You had me fooled.

--------
Oh alright, I did not know there was some kind of tests that they had to pass. Very weird. Anyway, I spend a few hours gathering up information on what Vista looked like and then just dove right into putting it into place, I don't think the look could really fool anyone if they are an ubuntu user. Anyway, Thanks 4 the information.

---

### Post by marc321 on 2007-06-18
> **Anonii said:**
> Windows Firefox passes the Acid2 test, but Linux Firefox doesn't?
Interesting.

You are right to question me.  Firefox 2 doesn't pass the test in either OS.

Yet another mistake for me today.  When I looked at the screen shots, I focused on the web page.  In the Windows screen shot, I just glanced at the actual browser and of course the first thing that registered in my mind was IE7.  The Firefox theme is a bit deceiving, but then again I'm tired and frustrated and didn't notice the Firefox in the title bar...

Time to go to bed.

---

### Post by TheVault on 2007-06-22
> **marc321 said:**
> You are right to question me.  Firefox 2 doesn't pass the test in either OS.

Yet another mistake for me today.  When I looked at the screen shots, I focused on the web page.  In the Windows screen shot, I just glanced at the actual browser and of course the first thing that registered in my mind was IE7.  The Firefox theme is a bit deceiving, but then again I'm tired and frustrated and didn't notice the Firefox in the title bar...

Time to go to bed.

--
Lol my bad. I like the Aero look in Firefox, so I went with the Vista them in Ubuntu. The screenshot with the black taskbar is Ubuntu, the one with with the blue taskbar is Windows. You can really tell a difference. Sorry if I made things hard on the eyes.

---

### Post by Anonii on 2007-06-22
I still don't get why the same (?) Firefox version gives problems in Linux and not in Windows.
Any ideas?

---

### Post by marc321 on 2007-06-23
Well, I've done a bit of digging through the site.  It uses a lot of advanced CSS code, along with something I've never heard of, [sIFR]("http://www.mikeindustries.com/sifr/") ("Scalable Inman Flash Replacement").  It is a method of replacing text elements in a page on-the-fly with Flash objects.  The benefit, supposedly, is that sites can use any font they want within these flash objects, eliminating the need for people to have that font installed client-side.

The link I provided above explains the process.

So, what it boils down to is the Linux Flash player.  I am not about to install the latest beta, as many have reported very unstable behavior, but maybe the problem will be fixed in the next release.  The Tamarin project by Mozilla (see [http://www.mozilla.com/en-US/press/mozilla-2006-11-07.html]("http://www.mozilla.com/en-US/press/mozilla-2006-11-07.html")) may also resolve some issues.

*sigh*

I can't wait until the time when the GNU/Linux market is large enough to be deemed profitable by major software and hardware companies.  I applaud companies like Adobe, NVidia, and Dell for taking a chance with Linux.  GNU/Linux is the future.  If nothing else, it will far outlast any proprietary software (Windows comes to mind).

---

