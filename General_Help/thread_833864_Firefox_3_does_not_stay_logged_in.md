---
title: "Firefox 3 does not stay logged in"
date: 2008-06-19
forum: General Help
---

### Post by agaudio on 2008-06-19
This is odd. I am a frequent user of Google services, so I often use the function "Remember me" when logging into a Google service. However, it seems that about once a day, this setting is forgotten by the Firefox 3 browser and I have to log in again. Even odder is that this problem does not seem to affect Firefox 3 on my other (Windows) computer. Seems to me the problem should be cookie related, but if I pull up the Google cookie, I can see it is years before it is supposed to expire.

Same thing happens for the RememberTheMilk Web site.

Can anyone shed any light on this?

---

### Post by Exsecrabilus on 2008-06-19
You don't happen to clear cookies when you clear your private data, do you?

---

### Post by SpenceMakesSense on 2008-06-19
this happens to me too. For me its with Xanga, Myspace, and gmail but not for the ubuntu forums.

---

### Post by yello_ubu on 2008-06-19
Same problem here. I pretty much find that all sites with a 'remember me' option don't. I don't have personal data cleared on quitting FF.

---

### Post by b5baxter on 2008-06-19
I am experiencing this problem with Netvibes and mail.yahoo.com

Firefox 3 Beta seemed to work fine.  Firefox 3 Final doesn't.

rob_

---

### Post by agaudio on 2008-06-21
Hmmm... interesting that I am not alone with this problem. I am not clearing personal data either when I close. And I just noticed some odd behavior. If I click on my CheckGmail icon up by the clock, the browser opens into Gmail no problem. And then all the other Google services are logged in. I guess that's not surprising, as CheckGmail probably submits the password when it opens the browser, thus logging me into all the Google services. Also, if I open directly into Hotmail via Pidgin, and then go to my homepage (Google News), I appear to be logged in. Now, that is a little odder, since these two services have nothing to do with each other....

---

### Post by agaudio on 2008-06-21
I think I may have discovered something and I am curious if anyone else experiences the same thing. My home page in Firefox is Google News. Usually, but not always, when I clean start the browser, I am not logged in - despite having selected "Remember me". However, if I simply click the refresh button for the page, then I am logged in. Somehow, it seems Firefox is not quite getting there when it loads the page the first time (something to do with how Firefox loads?) but when I refresh, whatever the problem was seems to have cleared itself up.

Can anyone else confirm this behavior?

---

### Post by myand on 2008-06-22
For me the inability to save logged-in sessions was caused by Torbutton. There are a lot of complaints concerning this already on Torbutton's Add-ons page.

---

### Post by agaudio on 2008-06-22
Odd. I don't use the Torbutton extension, but your post got me thinking about extensions in general. I realized that this problem showed up when I upgraded to Hardy - and thus Firefox 3, and that it might very well be a problem with some extension that wasn't fully insync with the new Firefox installation. I went in and disabled ALL of my extensions and checked. Sure enough, I stay logged in now. Then I went back and enabled each extension, one at a time, restarting after each enabling and checking to see if I stay logged in. The funny thing is that I stayed logge din after reenabling every extension. Now I have all my extensions enabled and I stay logged in. I am not sure what happened really, but perhaps one of the extensions I kept when upgrading to Firefox 3 needed to be "reset"?

Anyhow, I would suggest that anyone else who has this problem try out the procedure above to see if it helps solve the problem. I will keep an eye on things and report back if the problem returns.

---

### Post by agaudio on 2008-06-23
Nope. Problem returned. It worked well for a whole, but then the problem returned that I am not logged into my Google service when I start the browser with Google News as the homepage. But then I press refresh and I am logged in. How frustrating!!!

---

### Post by myand on 2008-06-23
Did you try disabling all the extensions again? It could be like you said, maybe one of them needed a 'reset' in order to make the logged-in sessions to work, but the fix isn't long-lasting, and so the only permanent solution is to isolate the extension causing this, and to disable it. Finding out the culprit could be a pain, though, if it really behaves that way...

But if it works without all the extensions (starting Firefox in Safe Mode is the easiest way to test this), I'd say you're likely to find the cause among them.

---

### Post by agaudio on 2008-07-06
I think I have finally localized the problem to the Gmarks extension. It appears that if you have the Gmarks extension set to automatically sign in when the browser start, then if you have some other Google service (Google News in my case) as your start page, it will start as not being logged in. However, if you click refresh, then it signs in. If you turn off automatic sign in for Gmarks, then the start page logs in automatically like it should, and usually, so does Gmarks. I assume this means Gmarks uses the same cookie as the Google services. Can anyone else confirm this?

---

