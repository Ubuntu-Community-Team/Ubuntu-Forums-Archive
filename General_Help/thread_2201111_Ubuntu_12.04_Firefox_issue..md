---
title: "Ubuntu 12.04: Firefox issue."
date: 2014-01-22
forum: General Help
---

### Post by Tsela on 2014-01-22
Hi everyone,

My partner has been running with a weird Firefox issue, and I'm at a loss on how to solve it. I'm now hoping someone else has experienced the same issue and can help me solve it.

My partner and I have separate accounts on our Ubuntu 12.04 desktop. We both use Firefox as our main browser. Today, when trying to make a payment via internet banking, he ran into a weird issue that prevented him from completing the payment (note: our bank just launched a new internet banking website): the site kept nagging him that the "amount" field was empty, despite the fact that it was clearly filled. No amount of tweaking helped. Even resetting his Firefox browser didn't help. A related issue was that autojump between fields didn't work on his browser either (if you're wondering what autojump is, check this page: [http://www.idocs.com/tags/forms/index_famsupp_162.html](http://www.idocs.com/tags/forms/index_famsupp_162.html)).

But now comes the weird part: on my account, with my Firefox browser, the internet banking website works just fine! And autojump between fields works perfectly! And the weirdest part is: I've heavily modified my Firefox browser, while he hasn't! He's nearly running it on factory settings! I've even checked via the guest account: Firefox on the guest account fails on the internet banking website and the autojump website as well!

I feel the world has turned upside down or something! My own, heavily modified, full of extensions version of Firefox works just fine, while Firefox on factory settings fails! What's up with that?!

And so that's why I'm asking the help of the community: I have no idea what the problem is. Since my browser works just fine, it's not simply a Firefox bug that I could send to Bugzilla. But since my browser works while being heavily modified, while factory settings versions of the browser fail to work, I have no idea where to look for a solution.

So, has anyone ever had that problem? (the autojump issue is a good test for it) If so, any idea how to solve it? Many, many thanks in advance!

Last note: the current version of Firefox on my machine is 26.0.

---

### Post by dragonfly41 on 2014-01-23
One suggestion is to try .. Firefox top bar > Help > Troubleshooting Information
and try "Reset Firefox to its Default State".

---

### Post by Tsela on 2014-01-23
> **dragonfly41 said:**
> One suggestion is to try .. Firefox top bar > Help > Troubleshooting Information
and try "Reset Firefox to its Default State".

I did that already, and even mentioned it in my post: "Even resetting his Firefox browser didn't help". Moreover, as I wrote, Firefox on the guest account (which is created on login and destroyed immediately after use, and thus is as pristine as possible, especially in term of Firefox settings) shows the same issue.

As I wrote, it's an issue for Firefox in its default, pristine, run-for-the-first-time state, but not for Firefox on my account, which is heavily modified with extensions and whatnots. Hence my problem: all issue-solving protocols for Firefox I've read have as underlying hypothesis that Firefox in its default state runs properly, and it's modifications and extensions that bring issues. My problem is exactly opposite!

Which is why I'm asking whether anyone else has had this issue before, because I'm at a loss on how I should handle it.

---

### Post by EnglishElectricAndy on 2014-01-23
A 'leftfield' guess from here is that it could well be a script issue with that page. As you stated the bank has only just set up their site it's likely to be a bit buggy, especially if they skimped on testing to meet some kind of commercial need or deadline.

Firefox extensions such as NoScript, Ghostery and the like will block, disregard or override such scripting issues whereas they would affect a default clean install of Firefox.

A possible suggestion is to contact the bank and ask them to pass the details to their IT dept or contractor. It definitely seems to me that problem lies at their end rather than with the customer.

Hope this is of help.

---

### Post by Tsela on 2014-01-23
> **EnglishElectricAndy said:**
> A 'leftfield' guess from here is that it could well be a script issue with that page. As you stated the bank has only just set up their site it's likely to be a bit buggy, especially if they skimped on testing to meet some kind of commercial need or deadline.

Firefox extensions such as NoScript, Ghostery and the like will block, disregard or override such scripting issues whereas they would affect a default clean install of Firefox.

A possible suggestion is to contact the bank and ask them to pass the details to their IT dept or contractor. It definitely seems to me that problem lies at their end rather than with the customer.

Hope this is of help.

True, and I'm thinking of contacting them if nothing else helps, but that doesn't explain why such a simple example site as [http://www.idocs.com/tags/forms/index_famsupp_162.html](http://www.idocs.com/tags/forms/index_famsupp_162.html) shows the same issue (cursor doesn't jump from field to field automatically, which is exactly what that page is about: explaining how to script this, with a simple (and one hopes bug free) example showing how it works). I'm pretty sure that issue is related to the error my partner gets on that banking site. In both cases, some scripting that should be bugfree seems to go awry on a clean install of Firefox but not on my install.

It does give me an idea to test the issue, but I won't be able to try it before tonight. I'll come back once I tried.

---

### Post by dragonfly41 on 2014-01-23
Perhaps try testing the example site in a "more pristine" mode .. i.e. safe mode?

[https://support.mozilla.org/en-US/questions/954197](https://support.mozilla.org/en-US/questions/954197)

---

### Post by Tsela on 2014-01-23
> **dragonfly41 said:**
> Perhaps try testing the example site in a "more pristine" mode .. i.e. safe mode?

[https://support.mozilla.org/en-US/questions/954197](https://support.mozilla.org/en-US/questions/954197)

Okay, tried it, with exactly the same results: running Firefox in safe mode on my account, the example site works perfectly. Trying Firefox in safe mode on my partner's account or a guest account, and it fails!

In fact, this is getting really surreal: I made a test by copying my Firefox profile to a guest account, effectively giving the guest account all my Firefox settings. The example site still failed!!! In other words, it seems not to have anything to do with the Firefox settings themselves: Firefox on my account works correctly, but not on my partner's account or the guest account, even if I copy my settings there. What is going on?!

---

### Post by dragonfly41 on 2014-01-23
Next idea .. if you are still keen on tracking this down .. you could try starting a new profile in firefox with command line argument [COLOR=blue]-no-remote

[/COLOR]p.s. there is a handy "profile switcher" add-on

oh .. I see you've already tried copying over a profile.[COLOR=blue]

[/COLOR]So I add another idea .. install [COLOR=blue]bleachbit[/COLOR] from Ubuntu software centre and (System Tools > Bleachbit) purge Firefox cache and cookies.[COLOR=blue]
[/COLOR]
Have you tried another browser such as Opera, Chromium etc.[COLOR=blue]


[/COLOR]

---

### Post by Tsela on 2014-01-23
> **dragonfly41 said:**
> Next idea .. if you are still keen on tracking this down .. you could try starting a new profile in firefox with command line argument [COLOR=blue]-no-remote

[/COLOR]p.s. there is a handy "profile switcher" add-on

oh .. I see you've already tried copying over a profile.[COLOR=blue]

[/COLOR]So I add another idea .. install [COLOR=blue]bleachbit[/COLOR] from Ubuntu software centre and (System Tools > Bleachbit) purge Firefox cache and cookies.[COLOR=blue]
[/COLOR]
Have you tried another browser such as Opera, Chromium etc.[COLOR=blue]


[/COLOR]

Okay, tried with the -no-remote argument, to no avail. Doesn't change anything :(. Frankly, I'm at a complete loss as to why one instance of Firefox would work correctly while the others don't, on the same computer! It just doesn't make any sense.

My last try (I use the Ibus input method on my account, while my partner's account doesn't, so I tried setting it up for him) failed as well. The input method, at least, seems to have no influence.

Frankly, I'm getting desperate here. Really, has nobody ever had this issue before?

I'll test other browsers, hopefully those won't behave as strangely as Firefox does...

---

### Post by Tsela on 2014-01-23
Okay, just tried Chromium. Exactly the same issue!!! Chromium on my account works perfectly. On my partner's account Chromium fails on the example site! So the issue is definitely not browser-specific but something else entirely. What can I do now?!

---

### Post by dragonfly41 on 2014-01-23
First .. to build up more diagnostic clues .. try this alternative approach ...

[http://digitalbush.com/projects/masked-input-plugin/](http://digitalbush.com/projects/masked-input-plugin/)

Does this work?

Next ... returning to Firefox (now we know it is not a Firefox only quirk) ... install Firebug add-on.

Now for each form session (your session and other user session) in the form field right click and "inspect element".

You can see what js is being applied to the form field(s).   See if you can spot any difference.

As a guess it does seem that the remote web service might be the problem .. perhaps not allowing multiple user sessions from the same computer or IP address?   Have you tried access from different laptops?  i.e. I concur with guess in post #4 in this thread.

---

